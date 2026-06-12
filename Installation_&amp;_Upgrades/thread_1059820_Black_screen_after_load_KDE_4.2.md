---
title: "Black screen after load KDE 4.2"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by SpreadFirefox on 2009-02-04
Hello,
I have upgraded to Interpid 8.10 with experimental KDE 4.2 and now when KDM loads KDE 4.2 screen after first two pictures on loading screen everything goes black. I have Intel 945 chipset on Optiplex GX 520 box.

---

### Post by abn91c on 2009-02-04
disabling desktop effects will get you in

---

### Post by SpreadFirefox on 2009-02-04
They are. If I try to enable them I get error message.

---

### Post by abn91c on 2009-02-04
> **SpreadFirefox said:**
> They are. If I try to enable them I get error message.
remove compiz if installed

---

### Post by agim on 2009-02-04
I had this problem earlier today. I ran the updates, which didn't initially work. So I restarted, which seemed to do the trick. Of course I don't know why it should or would. I am typing from kde 4.2 now, with kwin effects turned on. Compiz is also installed (I installed this with the original gnome desktop, and have left it untouched.)

---

### Post by filipn on 2009-02-21
I have the same problem after I turned the effects on.

Unfortunately I'm very new to Ubuntu and Linux in general, so I don't even know how I can turn the effects off now. I get the black screen when I log into kubuntu, so I can't turn them off the way I turned them on.

Is there any way to turn the effects off without logging on to the X window system (I believe that's what it's called)? When I tried Linux a couple of years ago (I think it was SUSE) there was the option to log in as root and control stuff from there, but apparently that is not possible now.

I'm sure there is a way to get a command line without logging in to the X window system and then turn the effects off, but I have no idea how.

Thanks for any help!

---

### Post by Perryg on 2009-02-21
> **filipn said:**
> I have the same problem after I turned the effects on.

Unfortunately I'm very new to Ubuntu and Linux in general, so I don't even know how I can turn the effects off now. I get the black screen when I log into kubuntu, so I can't turn them off the way I turned them on.

Is there any way to turn the effects off without logging on to the X window system (I believe that's what it's called)? When I tried Linux a couple of years ago (I think it was SUSE) there was the option to log in as root and control stuff from there, but apparently that is not possible now.

I'm sure there is a way to get a command line without logging in to the X window system and then turn the effects off, but I have no idea how.

Thanks for any help!

When booting press the escape key.  Select recovery mode.  There are a few things that you can do including shell in as root.  Man the items that are affecting you and see if there are any suggestions there.

---

### Post by diablillo77 on 2009-02-22
What's up guys?! 

Hey, I had the same problem and I followed a combination of fixes from Dutler and Altacus in another thread. 

After login, I had nothing but a blank screen and cursor. I pressed
   Ctrl+Alt (hold them down) then press "F2" key 
This brings you to a command line login screen, type your username, press "Enter", then your password, press "Enter"
after log in,  make sure KDE is stopped using this command:
   sudo /etc/init.d/kde stop

during the initial upgrade to 4.2, I had some errors and some packages didn't get installed so I did a
   sudo apt-get upgrade-dist -f

This told me "gwenview" was held back. People in the other thread had more packages held back, and advised to removed them all. I guess I was "lucky" it was only 1
   sudo apt-get remove gwenview

If you have more packages to remove, just type them all in this line separated by a space. I'm fairly new to command line, so if I'm wrong, please correct me.
   sudo apt-get remove package1 package2 package3 ... and so on.

Last, after removing all the packages that are held back, I installed kubuntu-desktop-- strange, but it wasn't installed. 
   sudo apt-get install kubuntu-desktop

which installed "gwenview" and everything else.

When kubuntu-desktop is finished installing, reboot using this command:
   sudo reboot
It might ask you for your password. If it does, type it in and your system will reboot right after.
When you system is back up, log in to an AWESOME KDE 4.2... Great job to everyone involved in KDE!!

I should've figured kubuntu-desktop was not installed properly because at the login, the only other login options were failsafe, and default-- no KDE. 

Hope this helps :D

---

### Post by Mrkijo on 2009-02-22
> **diablillo77 said:**
> What's up guys?! 

Hey, I had the same problem and I followed a combination of fixes from Dutler and Altacus in another thread. 

After login, I had nothing but a blank screen and cursor. I pressed "Ctrl+Alt+F2", logged in and made sure kde was stopped:
sudo /etc/init.d/kde stop

during the initial upgrade to 4.2, I had some errors and some packages didn't get installed so I did a
sudo apt-get upgrade-dist -f

This told me "gwenview" was held back. People in the other thread had more packages held back, and advised to removed them all. I guess I was "lucky" it was only 1

Last, I 
sudo apt-get install kubuntu-desktop
which installed "gwenview" and everything else, rebooted and logged in to an AWESOME KDE 4.2... Great job to everyone involved in KDE!!

I should've figured kubuntu-desktop was not installed properly because at the login, the only other login options were failsafe, and default-- no KDE. 

Hope this helps :D

I am very new to kubuntu and after upgrade I have the same problem, I have tried thing that are described above but somehow I could not make it work it seams to me that there is something else that needs to be done which you consider that is well known therefore I am begging you to put the solution in steps (as for dummies) .


Thanks - and sorry if some words are not correct since English is not my native language

---

### Post by diablillo77 on 2009-02-22
Mrkijo.. I updated my post with a few more details. Hope it helps!

---

### Post by Mrkijo on 2009-02-23
Unfortunately I have not succeeded, first thing that didnot worked for me is
sudo apt-get upgrade-dist -f (command not recognized)

And during the attempt of sudo apt-get install kubuntu-desktop

My computer cannot establish the connection in X mode via wireless?

---

### Post by Perryg on 2009-02-23
> **Mrkijo said:**
> Unfortunately I have not succeeded, first thing that didnot worked for me is
sudo apt-get upgrade-dist -f (command not recognized)

And during the attempt of sudo apt-get install kubuntu-desktop

My computer cannot establish the connection in X mode via wireless?

try:
**sudo apt-get dist-upgrade -f**

---

### Post by Mrkijo on 2009-02-25
OK that is the right command but the connection to internet could not be established, it might have to do something with the wireless that I am using, is there any command to establish a connection?

---

### Post by Perryg on 2009-02-25
> **Mrkijo said:**
> OK that is the right command but the connection to internet could not be established, it might have to do something with the wireless that I am using, is there any command to establish a connection?

Do an ifconfig and post the information to this.

---

### Post by 4ebees on 2010-04-29
> **Perryg said:**
> Do an ifconfig and post the information to this.

Hi all,

A friend was struggling with this on a laptop.

We finally renamed .kde

/home/<name>/.kde

to .kde.orig

and rebooted.

This, luckily, solved the problem.

---

