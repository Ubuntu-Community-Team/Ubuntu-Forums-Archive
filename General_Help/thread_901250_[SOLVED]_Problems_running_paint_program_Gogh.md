---
title: "[SOLVED] Problems running paint program Gogh"
date: 2008-08-26
forum: General Help
---

### Post by groundnut on 2008-08-26
I've downloaded Gogh to my home directory.
While in the sub directory Gogh-0.1.2.1, I gave the ./gogh command in order to run the program. This did not work. The following error was given.
ImportError: No module named ext
The complete response from the command line is shown below.

Doe anybody understand this?


tony@xp:~/Gogh-0.1.2.1$ ./gogh
Traceback (most recent call last):
File "./gogh", line 31, in <module>
from goghmain import GoghWindow
File "/home/tony/Gogh-0.1.2.1/goghmain.py", line 35, in <module>
from brushmanager import BrushManager
File "/home/tony/Gogh-0.1.2.1/brushmanager.py", line 30, in <module>
from settingmanager import *
File "/home/tony/Gogh-0.1.2.1/settingmanager.py", line 27, in <module>
import xml.dom.ext
ImportError: No module named ext

---

### Post by jamincollins on 2008-11-12
If you haven't already found the solution:

[http://ubuntuforums.org/showpost.php?p=5092404&postcount=5](http://ubuntuforums.org/showpost.php?p=5092404&postcount=5)

---

### Post by groundnut on 2008-11-13
thanks jamincollins,

I solved the problem already months ago with exactly the same page you are referring to.

---

### Post by jamincollins on 2008-11-13
There's also a packaged version here:

[https://launchpad.net/~mrkanister/+archive](https://launchpad.net/~mrkanister/+archive)

---

### Post by groundnut on 2008-11-13
Thanks very much jamincollins.

In December I will do a clean install of Intrepid Ibex.
I will use the package then.
However at the moment there seems to be a package for Hardy Heron only.

---

