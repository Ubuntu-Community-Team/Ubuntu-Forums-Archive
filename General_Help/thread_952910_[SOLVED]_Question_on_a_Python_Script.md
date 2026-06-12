---
title: "[SOLVED] Question on a Python Script"
date: 2008-10-19
forum: General Help
---

### Post by Nate9009 on 2008-10-19
I have been having some problems running a certain py script.  It's not finding a picture that *is* in fact there, and crashing as a result.  I'm positive it's the right image, and it's in the same folder as the python script.  Any ideas on what I should do?

Thanks!  

CLI output :

```
<edit>@<computer>:~$ python /home/<me>/Desktop/<app>/<the script>.py
Traceback (most recent call last):
  File "/home/<me</Desktop/<app>/script>.py", line 329, in <module>
    app = Queen(master=root)
  File "/home/<me>/Desktop/<app>/<the script>.py", line 273, in __init__
    self.run()
  File "/home/<me>/Desktop/<app>/<the script>.py", line 278, in run
    photo = PhotoImage(file='banner.gif')
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 3273, in __init__
    Image.__init__(self, 'photo', name, cnf, master, **kw)
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 3229, in __init__
    self.tk.call(('image', 'create', imgtype, name,) + options)
_tkinter.TclError: couldn't open "banner.gif": no such file or directory
> Removing 'stop' file
```

Any help is appreciated! :)

---

### Post by unutbu on 2008-10-19
Here are 5 options:

[list]
[*] cd to the directory with the image first:
```
cd /home/<me>/Desktop/<app>/
python <the script>.py
```

(Python adds the current directory to the list of directory it searches for files).

[*] Edit <the script>.py and put in these lines:
```

import os,sys
os.chdir(os.path.dirname(sys.argv[0]))
```

This changes the current directory to the directory that contains <the script>.py from within the python script.

Unlike the options below, it does not hard-code the path to the image. So if you move the directory containing the image and script, this will still work. The suggestions below will break.
[*] Edit <the script>.py and put in these lines:
```

import sys
sys.path.append('/home/<me>/Desktop/<app>/')

```

[*] Another option would be to add 

/home/<me>/Desktop/<app>/

to your PYTHONPATH environment variable, but that doesn't feel right to me.

[*] Edit the script, changing 'banner.gif' to the full absolute path to the file. (Blech.)
[/list]
(All the suggestions above assume that banner.gif is in /home/<me>/Desktop/<app>/.)

---

### Post by Nate9009 on 2008-10-19
> **unutbu said:**
> Here are 4 options:

1) cd to the directory with the image first:
```
cd /home/<me>/Desktop/<app>/
python <the script>.py
```

(Python adds the current directory to the list of directory it searches for files).

or 

2) Edit <the script>.py and put in this line:
```

import os,sys
os.chdir(os.path.dirname(sys.argv[0]))
```

(This changes the current directory to the directory that contains <the script>.py from within the python script.)

3) A third option would be to add 

/home/<me>/Desktop/<app>/

to your PYTHONPATH environment variable, but that doesn't feel right to me.

4) Edit the script, changing 'banner.gif' to the full absolute path to the file. (Blech.)

(All the suggestions above assume that banner.gif is in /home/<me>/Desktop/<app>/.)
Thanks very much!  Worked like a charm. :)

(also, I feel incredibly stupid for not realizing I was in the wrong directory in the first place...)

Thanks again!

---

