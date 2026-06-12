---
title: "Edit Menu problem"
date: 2008-07-24
forum: General Help
---

### Post by kakila on 2008-07-24
Hi all,
I have installed Hardy.
When I press right button of the mouse over the ubuntu symbol in the Panel and then click on "Edit Menus" nothing happens.
I read somewhere that alacarte would do the trick
```
sudo alacarte
```

and eveything works fine. Why I cannot acces alacarte using the option in the panel? Any solution? 

Thanks!

---

### Post by iaculallad on 2008-07-24
What about resetting your panel to default then try accessing "alacarte" using the right-click on Applications menu.

On your terminal:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

---

### Post by kakila on 2008-07-24
Thanks for the prompt answer.
I tried what you suggested but I still have the problem.
Clicking in the Edit menus does nothing.
BTW, jeje, my Network connections icon disappear from the panel and I cannot find how to put it back there (sorry for the newbieness).

Additionally, now alacarte shows a configuration of the menus that do not correspond to the actualmenu..??
There are some menu applications that fail to load.

---

### Post by iaculallad on 2008-07-24
> **kakila said:**
> Thanks for the prompt answer.
I tried what you suggested but I still have the problem.
Clicking in the Edit menus does nothing.
BTW, jeje, my Network connections icon disappear from the panel and I cannot find how to put it back there (sorry for the newbieness).

For the network icon: right-click on the top panel and select "Add to Panel", under the "System and Hardware", click on "Network Monitor" and click on Add button. That should restore the network connection icon.

---

### Post by kakila on 2008-07-24
Thanks again,Is not the Network monitor that is missing but the Network settings (where the wireless servers are listed).

Any suggestion for the unsynchronized menus?

---

### Post by iaculallad on 2008-07-24
> **kakila said:**
> Thanks again,Is not the Network monitor that is missing but the Network settings (where the wireless servers are listed).

Any suggestion for the unsynchronized menus?

My error; For the network manager icon: right-click on the top panel and select "Add to Panel", under the "Utilities", click on "Notification Area" and click on Add button.

---

### Post by inkrypted on 2008-07-24
You could try uninstalling and reinstalling Menu Editor from the add/remove under Applications and then reboot.

:)

Good Luck

---

### Post by kakila on 2008-07-24
> **inkrypted said:**
> You could try uninstalling and reinstalling Menu Editor from the add/remove under Applications and then reboot.

:)

Good Luck

As far as I know you cannot uninstall default applications using the Add/Remove...
Thanks anyway.

---

### Post by ad_267 on 2008-07-24
**Don't run alacarte as root.**

Use just "alacarte" not "sudo alacarte"

---

### Post by kakila on 2008-07-24
> **ad_267 said:**
> **Don't run alacarte as root.**

Use just "alacarte" not "sudo alacarte"
Thanks, but
```
user@laptop:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/juanpi/.config/menus/applications.menu'

```

---

### Post by iaculallad on 2008-07-24
> **kakila said:**
> Thanks, but
```
user@laptop:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/juanpi/.config/menus/applications.menu'

```

On your terminal:

```
sudo chown juanpi /home/juanpi/.config/menus/applications.menu
sudo chmod u+rw  /home/juanpi/.config/menus/applications.menu
```

Then:

```
alacarte
```

---

### Post by ad_267 on 2008-07-24
You get that error because you ran it as root in the first place.

---

### Post by kakila on 2008-07-24
> **ad_267 said:**
> You get that error because you ran it as root in the first place.

Mmm...maybe, but I run sudo the first time because I got this msg from the beginnig.

---

### Post by inkrypted on 2008-07-24
How about in synaptic can you choose to reinstall Menu Editor that might reset you permission problem.

---

### Post by kakila on 2008-07-24
Thanks iaculallad,
run both commands but I get the same msg...uh!

---

### Post by ad_267 on 2008-07-24
Can you post the output of "ls -l /home/juanpi/.config/menus/"

Also is your home directory on an ext3 partition? (This is the default so unless you set it up differently it will be)

---

### Post by kakila on 2008-07-24
Hi again,
Yeap, my /home is in a ext3 partition.
Here is the output of the command you suggested
```
juanpi@juanpi-laptop:~$ ls -l /home/juanpi/.config/menus/
ls: cannot open directory /home/juanpi/.config/menus/: Permission denied
```
if I do it with sudo
```
juanpi@juanpi-laptop:~$ sudo ls -l /home/juanpi/.config/menus/
total 12
-rw-r--r-- 1 juanpi root 1100 2008-07-24 10:18 applications.menu
drwx------ 2 root   root 4096 2008-07-14 14:35 applications-merged
-rw-r--r-- 1 root   root  224 2008-07-24 10:18 settings.menu

```

Thanks!

---

### Post by ad_267 on 2008-07-24
Ok try this then.

```
sudo chown -R juanpi /home/juanpi/.config
sudo chgrp -R juanpi /home/juanpi/.config
```

The -R is for recursive so it will make sure you own all the files in .config.

Also can you post the output of "ls -al /home/juanpi" just to make sure there are no other directories that are owned by root.

---

### Post by kakila on 2008-07-24
Thanks!
That solved the problme with the edit menu thing and alacarte.
Now everything is synchronized and working.
Why were this folders and files owned by the root user?

Here is the ouput of the command using grep.
```

[juanpi@juanpi-laptop:~$ ls -al /home/juanpi |grep root
drwxr-xr-x  4 root   root     4096 2008-07-09 11:35 ..
-rw-r--r--  1 root   root     1167 2008-07-09 13:18 .nvidia-settings-rc

```

Apparently the video card setting are also owned by the root, should I change that too?

---

### Post by ad_267 on 2008-07-24
No that's ok, my .nvidia-settings-rc is owned by root too, I think it's supposed to be.

I'm not sure why that directory would be owned by root. It could be caused by accidentally entering a wrong command or by running an application as root when it shouldn't be. Glad to hear it's working now though!

---

