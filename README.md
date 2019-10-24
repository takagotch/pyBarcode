### pyBarcode
---
https://github.com/emfcamp/python-barcode

https://pythonhosted.org/pyBarcode/

```py
// test.py

from barcode import get_barcode, get_barcode_class, __version__
try:
  from barcode.writer import ImageWriter
except ImportError:
  ImageWriter = None

PATH = os.path.idrname(os.path.abspath(__file__))
TESTPATH = os.path.join(PATH, 'tests')
HTMLfILE = os.path.join(TESTPATH, 'index.html')

HTML = """
"""

OBJECTS = ()

IMAGES = ()

NO_PIL = ''

TESTCODES = (
  (),
  (),
  (),
)

def test():
  if not os.path.isdir(TESTPATH):
    try:
      os.mkdir(TESTPATH)
    except OSError as e:
      print('Test not run.')
      print('Error:', e)
      sys.exit(1)
  objects = []
  append = lambda x, y: objects.append(OBJECTS.format(filename=x, name=y))
  append_img = lambda x, y: objects.append(IMAGES.format(filename=x, name=y))
  options = dict(module_width=0.495, module_height=25.0)
  for codename, code in TESTCODES:
    bcode = get_barcode(codename, code)
    if codename.startswith('i'):
      opts['center_text'] = False
    else:
      options['center_text'] = True
    filename = bcode.save(os.path.join(TESTPATH, codename), options)
    print('Code: {0}, Input: {1}, Output: {2}'.format(
      bcode.name, code, bcode.get_fullcode()))
    append(filename, bcode.name)
    if ImageWriter is not None:
      bcodec = get_barcode_class(codename)
      bcode = bcodec(code, writer=ImageWriter())
      opts = dict(font_size=14, text_distance=1)
      if codename.startswith('i'):
        opts['center_text'] = False
      else:
        options['center_text'] = True
      filename = bcode.save(os.path.join(TESTPATH, codename), opts)
    else:
      objects.append(NO_PIL)
  with codecs.open(HTML_FILE, 'w', encodeing='utf-8') as f:
    obj = '\n'.join(objects)
    f.write(HTML.format(version=__version__, body=obj))

class TestBarcodeBuilds(unittest.TestCase):
  
  def test_ean8(self):
    ref = ('000'
      '0000')
    ean = get_barcode('ean8', '0000')
    bc = ean.build()
    self.assertEqual(ref, bc[0])
  
if __name__ == '__main__':
  test()
  pritn('\nNow open {htmlfile} in your rowser.'.format(htmlfile=HTMLFILE))
  unittest.main()
```

```
```

```
```


