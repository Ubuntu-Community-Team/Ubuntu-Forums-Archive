---
title: "I can't install a python module"
date: 2008-11-09
forum: General Help
---

### Post by PharmaPhunk on 2008-11-09
Ok I'm having trouble installing pymsn. I got it working before, but for some reason I cannot get it working now. The required dependencies are:

python >= 2.4
python gobject >= 2.10.1
ElementTree >= 1.2.0 or cElementTree >= 1.0.5 or python >= 2.5
pyOpenSSL >= 0.6
pyCrypto >= 2.0.0 

I installed all of them doing the old "python setup.py build && sudo python setup.py install"
Now when I try to install pymsn It says it cannot import gobject, which is weird because I have installed. I then try sudo-ing it and I get a different error, one that says "from gobject.constants import *
ImportError: No module named constants"

So the problem here is that it cannot import the gobject module. But I HAVE installed, what could be the problem here? Why isn't it recognizing it?

---

