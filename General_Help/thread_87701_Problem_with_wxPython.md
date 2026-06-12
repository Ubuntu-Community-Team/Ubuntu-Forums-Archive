---
title: "Problem with wxPython"
date: 2005-11-08
forum: General Help
---

### Post by binarymelon on 2005-11-08
When I try and launch Picard I get the following error:

AttributeError: 'module' object has no attribute 'eUTF8'

I installed wxPython with the following script:

```
#!/bin/sh

VERSION=2.6.1.0

tar -xzf wxPython-src-$VERSION.tar.gz
cd wxPython-src-$VERSION
mkdir bld
cd bld
../configure --prefix=/opt/wx/$VERSION --with-gtk --enable-unicode --without-opengl
make $* && make -C contrib/src/gizmos && make -C contrib/src/stc $*
make install && make -C contrib/src/gizmos install && make -C contrib/src/stc install
cd ../wxPython-src-$VERSION
python2.4 setup.py build_ext --inplace --debug WX_CONFIG=/opt/wx/$VERSION/bin/wx-config WXPORT=gtk2 UNICODE=1 BUILD_GLCANVAS=0 BUILD_OGL=0 BUILD_STC=0 BUILD_XRC=0
cd ..
cp -rv wxPython /opt/wx/$VERSION
```

and launch picard with the following:

```
#!/bin/sh
export LD_LIBRARY_PATH=/opt/wx/2.6.1.0/lib
export PYTHONPATH=/opt/wx/2.6.1.0/wxPython
python /opt/picard/tagger.py

```

If anyone could maybe give me a little insight as to what's wrong it would be appreciated.

---

