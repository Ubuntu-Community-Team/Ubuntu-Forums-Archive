---
title: "After kernel update, Ubuntu boots up as Kubuntu"
date: 2005-11-22
forum: General Help
---

### Post by futz on 2005-11-22
This is odd. Did some updates today. After it finished, it informed me that it had updated the kernel and recommended rebooting. So I did.

To my surprise, the first graphic screen now says Kubuntu and is blue instead of brown. I was freakin out, cuz I like gnome but don't care for kde, but once it got to the actual desktop, nothing has changed. It's still gnome.

---

### Post by lorenco on 2005-11-23
What could have happened is that your system is now picking up KDM and not GDM ?

Check this file : "/etc/X11/default-display-manager" <- it would contain /usr/bin/kdm (you can edit it and change it to /usr/bin/gdm
(at your own risk ... though) ;-)

---

### Post by kverde on 2005-11-23
Same thing happened to me--except it says XUBUNTU.  How can I get this back to Ubuntu?  Its the very beginning startup process--right after grub.

---

### Post by towsonu2003 on 2005-11-23
[QUOTE=futz]This is odd. Did some updates today. After it finished, it informed me that it had updated the kernel and recommended rebooting. So I did.

To my surprise, the first graphic screen now says Kubuntu and is blue instead of brown. I was freakin out, cuz I like gnome but don't care for kde, but once it got to the actual desktop, nothing has changed. It's still gnome.[/QUOTE]

So it changed the splash screen??? That is interesting... Unfortunately I dont know how to tweak the splash screen... You might wanna file this as a bug, if no one can answer to it here... 

But your X is still gnome right? Which is good :) good luck with the splash, sorry I can't help...

As for 
>  What has happened is that your system is now picking up KDM and not GDM  , I disagree as you still have gdm (gnome). 

PS. me=newbie

---

### Post by futz on 2005-11-23
[QUOTE=lorenco]What could have happened is that your system is now picking up KDM and not GDM ?

Check this file : "/etc/X11/default-display-manager" <- it would contain /usr/bin/kdm (you can edit it and change it to /usr/bin/gdm
(at your own risk ... though) ;-)[/QUOTE]

Nope. It still says ```
/usr/sbin/gdm
```

All that has changed (I hope) is the splash screen.

Mighty odd...

---

### Post by openmind on 2005-11-23
Mine too. After the updates I'm getting The blue Kubuntu splash startup. I actually liked the brown Ubuntu one.

Any ideas?

---

### Post by matthewv on 2005-11-23
I think its actually the boot-up splash screen which has changed. Try reinstalling usplash-artwork, or uninstallin kubuntu-usplash-artwork, or xubuntu-usplash-artwork

---

### Post by Abandon on 2005-11-23
[QUOTE=matthewv]I think its actually the boot-up splash screen which has changed. Try reinstalling usplash-artwork, or uninstallin kubuntu-usplash-artwork, or xubuntu-usplash-artwork[/QUOTE]

Nope, also the gdm was still in place. Could it be related to the kernel?

---

### Post by mdbarton on 2005-11-24
Same problem here!  I have installed the kubuntu-desktop package so I could try gnome and kde, used to get the ubuntu splash, now after last nights update I get the kubuntu splash.  I still get gdm though, and both gnome and kde still run ok, so no major problem - sounds like some testing was missed prior to releasing the updates.

---

### Post by l.tambiah on 2005-11-24
I doubt a kernel update would make this happen. My update was fine, i have not had no problems, just like many others. I dont think this is a bug, it could be something you have installed previously.

---

### Post by wjp.reg on 2005-11-24
[QUOTE=l.tambiah]I doubt a kernel update would make this happen. My update was fine, i have not had no problems, just like many others. I dont think this is a bug, it could be something you have installed previously.[/QUOTE]

I posted this earlier .. [http://www.ubuntuforums.org/showthread.php?p=511587#post511587]("http://www.ubuntuforums.org/showthread.php?p=511587#post511587")

but nobody responded; a time-zone thing?

Could it be happening only on those systems that have both gnome and KDE desktops installed?  Just a thought.

---

### Post by l.tambiah on 2005-11-24
Could well be, i dont have any KDE related packages on my system, i prefer to keep it simply GNOME....But as to what has caused the problem, i am not sure.

---

### Post by wjp.reg on 2005-11-24
Hello all;

I posted a bug report and received the following which resolved the issue for me.

```
sudo update-alternatives --configure usplash-artwork.so
```

Select **usplash-default**, and then

```
dpkg-reconfigure linux-image-2.6.12-10-386
```

or whatever kernal you happen to be running.  The following returns that info for you:

```
uname -r
```

See bug report [https://bugzilla.ubuntu.com/show_bug.cgi?id=20032]("https://bugzilla.ubuntu.com/show_bug.cgi?id=20032")

---

### Post by Skoezie on 2005-11-25
[QUOTE=kverde]Same thing happened to me--except it says XUBUNTU.  How can I get this back to Ubuntu?  Its the very beginning startup process--right after grub.[/QUOTE]
Same problem here.

Startup runs fine & gnome still works normally. 

Will try wjp.reg's solution this afternoon

---

### Post by mdbarton on 2005-11-26
[QUOTE=l.tambiah]I doubt a kernel update would make this happen. My update was fine, i have not had no problems, just like many others. I dont think this is a bug, it could be something you have installed previously.[/QUOTE]

:confused: Strange that after the update I have more entries in GRUB then - 2.6.12-9-386 was there orignally, and when I select this one I get the normal splash.  2,6,12-10-386 was added by the update and I get the kubuntu splash.

Will try the fix

---

### Post by mdbarton on 2005-11-26
There's a typo in wjp.reg's solution - this is the solution from bugzilla:
> 
If you've installed the kubuntu packages on a stock Ubuntu install, then they'll
change the default splash picture. Try

sudo update-alternatives --config usplash-artwork.so

Select usplash-default, and then

dpkg-reconfigure linux-image-`uname -r`

However you need to do
> sudo dpkg-reconfigure linux-image-`uname -r`
as the last step

---

### Post by Skoezie on 2005-11-26
[QUOTE=Skoezie]Same problem here.

Startup runs fine & gnome still works normally. 

Will try wjp.reg's solution this afternoon[/QUOTE]
Worked great!

Only difference is that I had to run

> sudo update-alternatives --all

to get it fixxed, instead of

> sudo update-alternatives --configure usplash-artwork.so

---

