---
title: "No command-prompt without x-server?"
date: 2008-07-17
forum: General Help
---

### Post by thacursedpie on 2008-07-17
First of all I want to say that I am new to Ubuntu.

I am trying to install my nvidia drivers on my PC with the Hardy version ubuntu.

However, I need to exit the x-server to be able to install them.

Ok, I exit the x-server with "sudo /etc/init.d/gdm stop". The screen turns black, and looks like a command-prompt.

However, none of the commands work! I can type in:
"cd /home" nothing.
"pdw" nothing.

Why can't I type in commands?

And I don't download the drivers via the standard way (enable restriced drivers or something like that) because those drivers are bad (for my PC), it makes everything go extremely slow.

---

### Post by scragar on 2008-07-17
erm... use ctrl+alt+F1 to get to a terminal without X running on it, then install it there, go back to xtrl+alt+F7 to get back to the gui, restart graphics(ctrl+alt+backspace) to see if it worked.

---

### Post by thacursedpie on 2008-07-17
Ok, thank you, I will try that.

EDIT:
Ok, by pressing ctrl+alt+F1 I get in a terminal. It seems like X is still running; atleast, that's what the nvidia installer is telling me.
So I disabled X with "sudo /etc/init.d/gdm stop". That worked. Now I started the setup. That worked too.

During the setup however, an error occured; it seems like I have no libc header files installed, and I was told to install them from my distribution's libc development package.

I downloaded this package with synaptic, retried, and now the install worked!

BUT, for some reason these drivers are bad too :(. Everything is going slowww. I will try to un-install these drivers, because the do more bad that good.

---

### Post by bodhi.zazen on 2008-07-17
Log in if needed.

There are two alternates, however.

The first is to use the drivers from the repos.

sudo apt-get install nvidia-glx-new

Second is Envy

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by thacursedpie on 2008-07-17
The only issue is now: how to un-install the drivers?

My PC is too slow right now to do anything, so I need to first un-install the drivers before anything else.

---

### Post by bodhi.zazen on 2008-07-17
> **thacursedpie said:**
> The only issue is now: how to un-install the drivers?

My PC is too slow right now to do anything, so I need to first un-install the drivers before anything else.

Drop out of X

```
sudo sh NVIDIA* --uninstall
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

