---
title: "A few problems.."
date: 2008-08-04
forum: General Help
---

### Post by Bon Mots on 2008-08-04
I am currently running Hardy Heron but I am encountering some problems:

1. When booting up, no load bar shows up (Recently reinstalled OS, it worked before).

2. 4 out of 5 times the screen goes blank when it boots up and it just stays blank, keyboard won't respond either and no mouse cursor shows up.

Need some help please.. I'm kind of a newbie at Ubuntu, so please explain things out. Thanks

---

### Post by pytheas22 on 2008-08-04
> When booting up, no load bar shows up (Recently reinstalled OS, it worked before).

Does it display anything or just a blank screen (and if it's not blank, what is it saying)?  If you press control-alt-F1 do you see anything?

Second, how did you install Ubuntu (wubi or live CD)?

Third, have you looked in /var/log/syslog?  Do you see anything telling?  If not, please post the syslog here.
> 
4 out of 5 times the screen goes blank when it boots up and it just stays blank, keyboard won't respond either and no mouse cursor shows up.

Finally, if you press control-alt-F7 at this point, do you see anything?  If not, what does control-alt-backspace do?

---

### Post by Bon Mots on 2008-08-04
> **pytheas22 said:**
> Does it display anything or just a blank screen (and if it's not blank, what is it saying)?  If you press control-alt-F1 do you see anything?

Second, how did you install Ubuntu (wubi or live CD)?

Third, have you looked in /var/log/syslog?  Do you see anything telling?  If not, please post the syslog here.


Finally, if you press control-alt-F7 at this point, do you see anything?  If not, what does control-alt-backspace do?

1. It just displays a blank screen, and I haven't tried ctrl + alt + F1.

2. I installed it using live CD.

3. I haven't looked in /var/log/syslog either.. (how do I view it?)

4. I haven't tried the ctrl + alt + F7 or the ctrl + alt + bkspc

---

### Post by pytheas22 on 2008-08-04
> 1. It just displays a blank screen, and I haven't tried ctrl + alt + F1.
4. I haven't tried the ctrl + alt + F7 or the ctrl + alt + bkspc 

Please try them and let me know the results; they'll give an indication of where the source of the problem lies (failure of X to load, failure to switch you automatically to the right virtual terminal, or a video driver issue).
> 
3. I haven't looked in /var/log/syslog either.. (how do I view it?)

You can use the utility at System>Administration>System Log, or type:
```

gedit /var/log/syslog
```

Also, another question: what kind of video card do you have, and did you install any proprietary drivers for it or are you using whatever was installed by default with Ubuntu?

---

### Post by Bon Mots on 2008-08-04
I will try the ctrl + alt + F7 and the ctrl + alt + bkspc tommorow... however I was going to type in the command in termial, but my terminal is having problems, along with the systems log. I guess that's another problem. I'll try all of them tomorrow when I reboot the computer.

---

### Post by pytheas22 on 2008-08-05
Something's up if your terminal has issues too...what exactly is going on?

Anyway keep in mind that you can still view syslog by pressing control-alt-F2  (it should bring you to a prompt where you can log in) and typing:
```

cat /var/log/syslog | less
```

It will be a long file and not fun to view that way, but you can scroll up and down through it using the arrow keys and will hopefully find something that will allow us to trace down the issue.

By the way, you mention that this is your second install of Ubuntu (I think) and that it worked fine the first time?  You may want to just wipe everything and install again (check your CD for defects first; there's an option to do this at the boot screen); it could be that something weird happened with this installation.

---

### Post by pauper on 2008-08-05
"less" will suffice :):

```
less /var/log/syslog
```

---

### Post by Bon Mots on 2008-08-05
Okay, so the ctrl + alt + F7 and the ctrl + alt + bkspc have no effect on the blank screen during the boot up. (I don't think they keyboard had an effect, the num lock light wouldn't turn on as it normally would)

pytheas22- My terminal/some other applications have problems sometimes, but it works fine right now.

The syslog is attached (it was too big so I attached it in 3 pieces).

Thanks for the help

---

### Post by pauper on 2008-08-06
Please, save your attachments, where appropriate, as plain text (.txt)--not
everyone around is using OpenOffice.org or MS Office.

```
gksudo gdmsetup
```

"Security" tab, check "Enable debug messages to system log". Turn it off later.

Now see through /var/log/debug, /var/log/messages and /var/log/syslog for any
gdm warnings and errors.

Attach:

/var/log/Xorg.0.log
/etc/X11/xorg.conf
~/.xsession-errors

Post the output:

```
lsmod
dmesg | grep drm
glxinfo
ldd `which glxinfo`
```

You might have some problems with GDM greeter startup. Look for errors:

```
sudo apt-get install xnest
export DOING_GDM_DEVELOPMENT=1
Xnest -display :1 & /usr/lib/gdm/gdmlogin
Xnest -display :1 & /usr/lib/gdm/gdmgreeter

# Press Ctrl-c to exit

unset DOING_GDM_DEVELOPMENT
```

---

### Post by Bon Mots on 2008-08-06
Oh, sorry about not saving it in .txt, should I go change them?

And  how can I tell what the errors are in the syslog?

---

### Post by hyper_ch on 2008-08-06
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by pauper on 2008-08-06
> **Bon Mots said:**
> And how can I tell what the errors are in the syslog?

Look for "warning" and "error" entries (not case sensitive).

> **Bon Mots said:**
> Oh, sorry about not saving it in .txt, should I go change them?

Open your *.doc files, highlight and copy data (Ctrl-a, Ctrl-c should work for
that, I suppose).

Applications--Accessories--Gedit

Paste (Middle-click). Save (Ctrl-s). Append *.txt. Press Enter.

Press "Edit" button (post #[noparse]8[/noparse]), then "Go Advanced". Scroll down to Additional
Options field, press "Manage Attachments". Inside of "Manage Attachments"
window click on "Remove". Then add txt copies.

In the future...

```
file -i /var/log/syslog
/var/log/syslog: text/plain; charset=us-ascii
```

It's a plain text by default. All you have to do is to append *.txt to make it
valid for upload:

```
cp /var/log/syslog ~/syslog.txt
```

Then just browse to location and click "Upload". If the size of file is beyond
provided upload limit create an archive beforehand.

---

