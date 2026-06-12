---
title: "[SOLVED] loss of Applications in menu bar"
date: 2008-08-29
forum: General Help
---

### Post by mike g on 2008-08-29
I am running 8.04 on an Intel Pentium 4 at 1.60 ghz with 503 MB or so of memory.

Kernel 2.6.24-19-386

My system crashed.  I am unable to open the "Applications menu" in the task bar.

My processor runs continually at near 100 %.

My disk drive went from 40% to 100% full without anything being added to it.

I am unable to shut down or reset the computer unless I physically turn it off at the on off switch.  If I use the menu bar shutdown I lose both menu bars but the desktop wall paper remains.  I am unable to get the menu bars back.

I have to manually enable my internet connection under "Network."

None of my on line applications will work.

Does anyone have any idea where I can start to fix this thing.  :confused::confused:

---

### Post by iaculallad on 2008-08-29
Try restoring your original panels:

```
sudo gnome-session-remove gnome-panel
sudo gconftool-2 --recursive-unset /apps/panel
sudo gnome-panel &
```

---

### Post by mike g on 2008-08-29
thanks I tried that and after the first line I got  "could not connect to session manager"

---

### Post by iaculallad on 2008-08-29
> **mike g said:**
> thanks I tried that and after the first line I got  "could not connect to session manager"

Try reading this [thread]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/237872") from bugs.launchpad if it could help you resolve the issue on "Could not connect to Session manager".

---

### Post by mike g on 2008-08-30
none of those seemed to help however I also am unable to connect to the sessions manager.....There seems to be, many things wrong with the system.

One additional thing...I set up a visitor log in for someone and after they used it these problems seemed to appear.  I removed the visitor from the group but apparently that simply does not remove all the programs involved with the visitor.  I hope that made sense.

My biggest problem, I have almost no knowledge of computer programing and workings.

---

### Post by SunnyRabbiera on 2008-08-30
can you give us details on your system?
specs?
what you installed and such?

---

### Post by mike g on 2008-08-30
My system is as stated above....I am using firefox3 and thunderbird as the mail client.

It is basically as it was in the initial download when I upgraded.  I added Kopete mkymoney, bluetooth, fire starter but that is about it.

Like I said I added another user login and that is when my problems started.  It is a pretty straight forward setup, not even any desk top effects used.

I was able to get a gnome-terminal by using alt F2 etc.

---

### Post by mike g on 2008-09-02
ok, now this is real strange.

Everything except the "Applications" menu now works.  I just do not understand....really I don't.

I still need help with getting the applications menu to work.

I am so stinking:confused::confused::confused::confused:

---

### Post by mc4man on 2008-09-02
> getting the applications menu to work.
If you mean that applications is still there but doesn't drop down then see here
[http://ubuntuforums.org/showthread.php?t=908167](http://ubuntuforums.org/showthread.php?t=908167)

---

### Post by mike g on 2008-09-04
I thank you but it seems as if I have more problems than I can handle.  I am back to no disk space when I had about 10 gigs this morning.  

I believe it is time for me to go back to windows.  It is very apparent that even though this system is supposed to be user friendly you need to have more than a general knowledge of computers and a working knowledge of computer programing to make it work.

Good bye Ubuntu..the trip was fun but in the end windows world won.

---

### Post by mike g on 2008-09-27
After much hair pulling and swearing my problem kept getting worse and worse....I am not sure how this happened but I was actually able to get the HD to boot once and once was enough to get in and delete several programs and my trash.  This allowed me to transfer all the important stuff to a USB stick...or e-mail myself with things that needed saving.

I reinstalled 8.04 off a disk....and am now trying to make Ubuntu work again.

I thank all of you for your attempts at assistance but the problem changed so much I was unable to give an exact account of my ever expanding problems.
I can only guess that my HD allocation table picked up a virus but my abilities are so outdated I could not tell if this was true.

One more try.....

Thank you all again.

Mike

---

