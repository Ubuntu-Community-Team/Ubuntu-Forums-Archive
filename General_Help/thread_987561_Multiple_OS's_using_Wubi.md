---
title: "Multiple OS's using Wubi"
date: 2008-11-19
forum: General Help
---

### Post by trxgt05 on 2008-11-19
Before I go all out with partitioning to do a dual boot of windows XP and Ubuntu, I've decided to use Wubi to do the install. I was curios if I could use Wubi to install Ubuntu and [K]Ubuntu simultaneously until I decided which I like best or does Wubi only do one at at a time? Basically, is this possible with Wubi or will it try to overwrite Ubuntu with [K]Ubuntu or vice versa?

---

### Post by OMJD on 2008-11-19
> **trxgt05 said:**
> Before I go all out with partitioning to do a dual boot of windows XP and Ubuntu, I've decided to use Wubi to do the install. I was curios if I could use Wubi to install Ubuntu and [K]Ubuntu simultaneously until I decided which I like best or does Wubi only do one at at a time? Basically, is this possible with Wubi or will it try to overwrite Ubuntu with [K]Ubuntu or vice versa?

Whilst this doesn't directly answer your question, I thought I'd point out that Ubuntu uses the Gnome graphical user interface, which is more stable than KDE. I suggest using Ubuntu.

I used to always prefer KDE when I was very new to Linux, I thought it looked better by default. But whenever I test it, it always seems to be much less stable than Gnome.

---

### Post by trxgt05 on 2008-11-19
Yeah I've been doing some research and that's what most people have been saying, but I'd like to find out for myself. I've heard KDE is easier to adapt to if you're used to windows(which I am)and I was thinking at least I could use it until I became more familiarized with the platform.

The thought just occurred to me that I could probably burn the boot CD's and just boot from them until I decided which GUI to stick with for the time being. Still my original question is unanswered.

---

### Post by wadelewis4 on 2008-11-19
I would say yes. You should be able to install both with wubi, given the way that it just appends the installation to the windows boot configuration and runs kind of like a vm. Install one, then reboot and finish the installation of the first distro, then reboot and repeat with the next one.

If all works well you should see this list at your windows boot selection:

Windows 
Ubuntu
Kubuntu (or it may identify itself as Ubuntu also)

Side note: You won't know for sure that it is or isn't going to work until you try it. The Wubi installer either will or won't let you install 2 releases. But like I said before, I would have to lean more toward yes.

---

### Post by trxgt05 on 2008-11-19
That's what I was leaning (and hoping) towards myself. I just haven't been brave enough to try it yet and was hoping to get a more affirmative answer. Maybe I'll try it soon. I'll be sure to post how it goes once I do unless there's someone out there that has already tried and knows for sure.

---

### Post by trxgt05 on 2008-11-21
Ok I tried installing both with Wubi and here's what happened:
1. I installed Ubuntu.
2. Restarted and booted in Ubuntu and let it do it's thing getting itself set up.
3. Restarted and booted in windows.
4. Tried to run Wubi again and the only option given was to remove the Ubuntu folder.
5. In an attempt to trick it, I renamed the Ubuntu folder.
6. I re-ran Wubi and the trick worked so I then installed Kubuntu.
7. I restarted, booted in Kubuntu and let the setup do its thing.
8. It automatically restarted after setting up and I booted in Kubuntu again to play with around with it. After the load screen it hangs and everything is unresponsive.

I ended up having to just flip the switch on it and reboot. Tried Kubuntu again and got the same results. Then I booted windows again and went to the directory where I installed them. Come to find out that it installed Kubuntu in a folder named ubuntu. I doubt this has anything to do with why Kububtu wouldn't work but it does prove that you probably can't install both U and K using Wubi, except possibly on different drives.

On a side note, I really don't know why Kubuntu didn't work because I ran it off a live CD just fine.

---

### Post by wadelewis4 on 2008-11-28
I see, well here's an idea: What about trying a virtual machine? 

Just install VirtualBox and create a new virtual machine to run Ubuntu on while in your Kubuntu wubi install. The reason for that would be that since KDE 4.1 is more resource hungry, you could just run Ubuntu, with the less resource intensive desktop environment, gnome, in the virtual machine and you could literally try both distros simultaneously. 

OR

Even better, if you just want to try both - like a time trial with each - just install one with Wubi, say ubuntu, then while using ubuntu open the terminal and type in the following line followed by the enter key.

```
sudo aptitude install kubuntu-desktop
```

Now you'll have the option at your login window to change session types between KDE and Gnome as you like.

---

### Post by ago on 2008-12-01
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20multiple%20distros?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20multiple%20distros?)

---

