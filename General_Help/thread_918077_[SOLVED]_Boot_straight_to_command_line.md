---
title: "[SOLVED] Boot straight to command line?"
date: 2008-09-12
forum: General Help
---

### Post by gldearman on 2008-09-12
Hi,

I would like to have the option, upon booting my system, of going straight to the command line and not launching any sort of GUI environment.  I don't *always* want to bypass the GUI, so I'd like to have either option -- go straight to the command line, or launch XWindows and Gnome -- when I start the computer.

I know that I can use recovery mode to get a root shell, but I don't need root access -- just a simple login to a shell with the user's normal permissions.

I have no clue how to do this.  I'm guessing that I am going to have to do something in GRUB to change the GRUB menu.  If that is the case, I would like to leave the normal (GUI) option as the default one.

Can anyone please point me in the right direction?  And, while you are at it, maybe point me to a good online resource on how to use the GRUB command line?

Thanks

---

### Post by tekky on 2008-09-12
Another option is to have the GUI turned off, so when you boot up into the CLI mode you can always just type: sudo /etc/init.d/gdm start
It's what I use because I'm based in CLI (server) Ubuntu.  So I barely use the GUI but when I do I just run it.  And to kill it, it would be sudo /etc/init.d/gdm stop

So it's pretty easy to turn it off and on instead of messing with the boot menus.  Simplicity seems to be the best answer in most cases.

Hope it helped.
-T

---

### Post by gldearman on 2008-09-12
> **tekky said:**
> Another option is to have the GUI turned off, so when you boot up into the CLI mode you can always just type: sudo /etc/init.d/gdm start
It's what I use because I'm based in CLI (server) Ubuntu.  So I barely use the GUI but when I do I just run it.  And it kill it, it would be sudo /etc/init.d/gdm stop

So it's pretty easy to turn it off and on instead of messing with the boot menus.  Simplicity seems to be the best answer in most cases.

Hope it helped.
-T

So, what you're saying is the easiest way is to *always *log in straight to the command line?

It is an option, but I also have other users on my system who *just *want the GUI, and would fall somewhere on the spectrum of confused to inconvenienced if they had to start it up every time. Besides which, none of them are administrators, so they don't have permission to run gdm start or gdm stop if it requires superuser powers.

Still, it is an option, thanks -- but how would I set up my system so that it bypassed the GUI on every login?

And, does anyone have an alternative solution that would better fit what I am trying to do?

Thanks.

---

### Post by gldearman on 2008-09-12
> **bingoUV said:**
> By some depravity of mind, Ubuntu developers disabled a simple way of doing what you want. In debian and many other distributions, you just add a "3" at the end of your grub command line, and you boot into a text only desktop. i.e.

1. Press 'e' on grub command line
2. Choose the line starting with kernel
3. Press 'e' again
4. Go to end of line and press space, and then 3
5. Press enter
6. Press 'b' to boot
Done.

With Ubuntu, I think you need to edit startup scripts to enable this.

OK, forgive me if I sound like a complete newbie -- is that the same as booting to runlevel 3?

---

### Post by bingoUV on 2008-09-12
> **gldearman said:**
> OK, forgive me if I sound like a complete newbie -- is that the same as booting to runlevel 3?

Exactly. But the Ubuntu developers had lost use of their senses to such an extent that they made all runlevels equal (except 0, 1 and 6 hopefully). So even if you boot into runlevel 3, you would find gdm in all its graphical glory.

---

### Post by rbc on 2008-09-12
Forgive me if you have thought of this already, but if you end up having to go this route (having GUI turned off by default), you could edit the /etc/sudoers file, to give those users permission to only run that superuser command (to start gdm). Word of caution, you can only edit the sudoers file with the vi text editor. Spend a day learning to use it

---

### Post by gldearman on 2008-09-12
> **rbc said:**
> Forgive me if you have thought of this already, but if you end up having to go this route (having GUI turned off by default), you could edit the /etc/sudoers file, to give those users permission to only run that superuser command (to start gdm). Word of caution, you can only edit the sudoers file with the vi text editor. Spend a day learning to use it

Yeah, I knew that I *could * edit sudoers to give them permission -- I've edited it once before.  I'd have to get some help, probably -- all the online tutorials on visudoers I have found left me more confused than when I started.  It still wouldn't help my other users know what to do when they got to a text prompt.  I'm the only real "power user" (and I use that term loosely) here.  My wife would be able to learn and enter the command every time, but I don't want to annoy her with the inconvenience.  So, I'd rather have a better option.

Oh, and I still don't know *how *to turn GUI off by default.

vi, at least, is no problem.  I had to use vi when I was in college -- in between hunting for mammoths and trying to discover fire.  It all comes right back to you, even if you've been away from it.

Thanks.

---

### Post by Sycron on 2008-09-12
I think you can do that with *rcconf*. Install it, is in the repos.

---

### Post by gldearman on 2008-09-12
> **Sycron said:**
> I think you can do that with *rcconf*. Install it, is in the repos.

O.K.  I will.  Thanks.

I can't try that until I get home, but I'll let you know if it works out.

Just one clarification -- by "do that," do you mean set up my system to bypass GUI on every boot by default, or do you mean that I will be able to set one runlevel to be command-line only, but leave another GUI?

Thanks again!

---

### Post by Vivaldi Gloria on 2008-09-12
To stop gdm from starting: restart your computer and press ESC to see grub boot menu. Choose recovery to boot to a recovery console. Give the command

```
update-rc.d -f gdm remove
```

and restart using the command

```
reboot
```

Now gnome won't start automatically from now on. You can start gnome with one of

```
startx
sudo /etc/init.d/gdm start

```

when you want.

Also, in ubuntu there there is NO difference between runlevels 2-5 including 3. In these runlevels all filesystems listed in /etc/fstab are mounted, desktop environment (if installed & configured) is started.

Finally, see my post [here]("http://ubuntuforums.org/showthread.php?t=917087") to learn how to edit sudoers:

---

### Post by gldearman on 2008-09-12
Thank you to Vivaldi Gloria (even if I am more of a Wagner man, myself).

But, just for clarification, when you say
> **Vivaldi Gloria said:**
> 
Also, in ubuntu there there is NO difference between runlevels 2-5 including 3. In these runlevels all filesystems listed in /etc/fstab are mounted, desktop environment (if installed & configured) is started.

Does that mean that there is no way to change that?  rcconf, for example, appears to be a runlevel configuration tool.  Would it, or some other tool, be allowed to change one of the runlevels, while leaving the others as is?  Or is this an immutable feature of Ubuntu?

Thanks! (Especially for the much easier tutorial on how to edit sudoers.)

---

### Post by Vivaldi Gloria on 2008-09-12
You can change runlevel properties simply with

```
sysv-rc-conf
```

You may need to install it first. You can configure different runlevels to have different properties.

Actually you can do everything you want with update-rc.d if you want.

I suggest you read the following links carefully (especially part 2):

[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/](http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/)
[http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/](http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/)

See also the man pages of the above commands.

I've never used rcconf so I cannot comment on it.

---

### Post by gldearman on 2008-09-12
Thanks!

---

### Post by Malac on 2008-09-16
.

---

