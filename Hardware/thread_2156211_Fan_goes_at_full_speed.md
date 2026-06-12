---
title: "Fan goes at full speed"
date: 2013-06-20
forum: Hardware
---

### Post by dpedro on 2013-06-20
Hi guys, 
im sorry if anything is not acording to what its suposte to do i am new in this thing's of linux or forum and sorry again for my rusty english.
Here it is my problem when i put my laptop its an HP 6730b [Intel® Core™2 Duo CPU P8400 @ 2.26GHz × 2, Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 and i have installed ubuntu 13.04 whit windows 7 at the same time] but my problem is when i suspend my laptop when i restore again the fan goes at maximu speed and continue for ever until i shutdown, more strange is that the air that come out of the fan its cold so i think its not a problem of overheating.
im a tired of shuthing of my pc...


thank you

---

### Post by Toz on 2013-06-20
Hello and welcome to the forums.

There is an existing bug report for this exact problem. See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173997]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173997").

Can you try the **acpi_osi=Linux** kernel parameter? See the "Kernel Boot Parameters" link in my signature for information on how to test the parameter. It would also be interesting to see your dmesg log file. From a terminal window, enter this command:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by dpedro on 2013-06-21
hi again Toz, how stupid is that im not able to type "=" on the kernel boot parameteres im using a portuguese keyboard and i tryed every single key and the equal dont show up :S 
so thats why i cant post back the link. any sugestion to solve this keybord problem?

---

### Post by Warprunner on 2013-06-21
a workaround... you could type it in your phone as an email.. save as draft. Then access your email on your computer and copy the text.

Silly...but it will work.

---

### Post by dpedro on 2013-06-21
but on ubuntu i am able to type "=" only on kernel parameters window when i start the system im not able to type the equal, and i dont know how to copy on the terminal

---

### Post by Toz on 2013-06-21
> **dpedro said:**
> hi again Toz, how stupid is that im not able to type "=" on the kernel boot parameteres im using a portuguese keyboard and i tryed every single key and the equal dont show up :S 
so thats why i cant post back the link. any sugestion to solve this keybord problem?

Try following the instructions under "Permanently Add a Kernel Boot Parameter" from within an ubuntu session. Your = key should work there. Make sure to run the "sudo update-grub" command as well then reboot.

---

### Post by dpedro on 2013-06-22
It worked men here it is dmesg log file, should i remove the kernel parameter?
[http://paste.ubuntu.com/5789972/](http://paste.ubuntu.com/5789972/)
this is enought to solve the problem ?

---

### Post by Toz on 2013-06-22
> **dpedro said:**
> It worked men here it is dmesg log file, should i remove the kernel parameter?
[http://paste.ubuntu.com/5789972/](http://paste.ubuntu.com/5789972/)
this is enought to solve the problem ?

Does this solve your fan problem? If so, you'll need to leave the kernel parameter there (don't remove it).

---

### Post by dpedro on 2013-06-23
but it doesnt work like that :P unfortunately my fan continue going the same after suspend :S

---

### Post by Toz on 2013-06-23
In that case, you can remove the kernel parameter.

Lets try this (from [this kernel bug report]("https://bugzilla.redhat.com/show_bug.cgi?id=895276")):

```
gksu gedit /etc/pm/sleep.d/99_fanfix
```
...then copy/paste this code:
```
#!/bin/bash
case $1 in
        thaw|resume)
           for x in /sys/class/thermal/cooling_device*/cur_state; do
              echo 0 > $x
           done
        ;;
esac
```
..then save the file and make it executable:
```
sudo chmod +x /etc/pm/sleep.d/99_fanfix
```

Now try a suspend/resume and see if the fans behave.

---

### Post by dpedro on 2013-06-24
Toz thank you so much, i think it work very well lets see if goes ok in long time, hope so again thank you so much

---

