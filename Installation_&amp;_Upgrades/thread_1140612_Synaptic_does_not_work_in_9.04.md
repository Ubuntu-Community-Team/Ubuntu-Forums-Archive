---
title: "Synaptic does not work in 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by 0x414141 on 2009-04-27
Hello, 

  I updated from Hardy to Jaunty yesterday. Since, many of my applications are broken, mostly synaptic and deluge. It may very well be the same bug or two different. 

When i click on synaptic manager (System --> Administration --> Synaptic Manager), i receive a prompt for my password. I enter my password and nothing happens. 

From the command line, if i sudo synaptic, here is the output i receive: 
```

[sudo] password for 0x414141: 
No protocol specified

(synaptic:8817): Gtk-WARNING **: cannot open display: :0.0

```
I also have this weird gtk error when i try to start Deluge (hence the .. it might be related)

```
deluge
[ERROR   ] 20:39:48 ui:84 /usr/lib/libgio-2.0.so.0: undefined symbol: g_poll
Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/deluge/ui/ui.py", line 65, in __init__
    from deluge.ui.gtkui.gtkui import GtkUI
  File "/var/lib/python-support/python2.6/deluge/ui/gtkui/gtkui.py", line 44, in <module>
    import gtk, gtk.glade
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libgio-2.0.so.0: undefined symbol: g_poll
[ERROR   ] 20:39:48 ui:85 There was an error whilst launching the request UI: gtk
[ERROR   ] 20:39:48 ui:86 Look at the traceback above for more information.
```I know this makes a lot of errors. I would rather give you more instead of less. 


While synaptic does not work, i can still apt-get without problems.  Can anyone help me?

---

### Post by cariboo on 2009-04-27
Open a terminal and type:

```
sudo apt-get -f install
```

This will install any missing dependencies or partially installed packages, then type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by smartmart on 2009-04-29
> **cariboo907 said:**
> Open a terminal and type:

```
sudo apt-get -f install
```

This will install any missing dependencies or partially installed packages, then type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

i have same error. :( ( after system update to 9.04)
```
arts@localhost:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libgio-2.0.so.0: undefined symbol: g_poll
marts@localhost:~$ 

```
reinstalling glib gtk ubuntu-desktop doesn`t works( 
p.s.
sorry for my bad eng.

---

### Post by gadgeX on 2009-04-29
I'm getting the same error with synaptic amounst other things .. I try sudo apt-get -f install and I get $Segmentation faultsts... 0%


also now an error checking for updates .

---

### Post by nandemonai on 2009-04-29
Correct upgrade path is 8.04 -> 8.10 -> 9.04.

That being said seems plenty of people are having issues with upgrades this release.

My suggestion would be to back up all your stuff and do a clean install.

/home/ on a separate partition? If not now might be a good time to consider it. ;)

---

### Post by 0x414141 on 2009-05-02
Thank you for your help. On my end, i did a reinstall, which was more time effective.

Thank you for your help once again.

---

### Post by chanthru on 2009-08-17
I hit the same error while opening synaptic. I ran following commands, after works fine for me.

sudo apt-get update
sudo apt-get upgrade

~Thanks
Chan

---

### Post by Phezz on 2009-08-20
I have a similar problem - 9.04 - only Synaptic fails.

apt-get works fine, but doesn't fix the problem

I recently tried to install a new theme - but I didn't delete any files, so I'm at a loss.

I've tried
> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install


Interestingly if I run synaptic as a normal user - it works...
> synaptic
I'm guessing that means root is messed up somehow... but it's 'disabled'

---

