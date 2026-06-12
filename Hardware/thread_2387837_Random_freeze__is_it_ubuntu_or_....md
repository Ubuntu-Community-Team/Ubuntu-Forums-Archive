---
title: "Random freeze : is it ubuntu or ... ?"
date: 2018-03-24
forum: Hardware
---

### Post by pierreb24 on 2018-03-24
Hello,

Once in a while (something like once a day, but I'm not using my desktop all day long), my Ubuntu gets totally frozen: cannot move the mouse, cannot type anything (even ctrl+alt+f1), cannot connect from another computer trough ssh, nothing (and when i unplug and plug the screen, it just shows back the same image). When I looked into the forum, I saw that a lot of those problem where caused by using Wayland ... But I'm not, so "this solution does not works for me" ^^. There does not seems to be a recurrent pattern (it can happen at any point) and the log does not seems to report anything interesting (dmesg & journalctl generally contains nothing at the time of the freeze).

I'm currently running ubuntu 17.10, with cinnamon and a nvidia driver. Since I cannot find anything, I'm starting to wonder whether it could not be a hardware isssue, but the question is ... How could I know? Does someone have any idea?

Thanks in advance,

Pierre

---

### Post by pierreb24 on 2018-03-24
Update: I got a lot (!) of freeze while working on a project with kdenlive. Therefore ... Could it be audio card ? Or video card ? Or ... Hard drive ? (and how could I know?)

---

### Post by cruzer001 on 2018-03-24
I also have this random freeze thing going on (I'm running 18.04).  We are both running xorg.  Your running the nvidia driver and I'm running nouveau.  I have read in this forum that modesetting may be a better choice for the both of us.  Don't know for sure, I haven't tried it yet.

[https://ubuntuforums.org/showthread.php?t=2385770](https://ubuntuforums.org/showthread.php?t=2385770)

It also discuss a newly release driver toward the end of the thread.

Nothing concrete here, just my thoughts on something you may want to try.

---

### Post by cybrsaylr on 2018-03-24
I also have this random freeze thing going on running 16.04 LTS Unity. It does seem to happen occasionally when online using Opera  51.0 browser on some sites. So not really sure if it's and Internet, browser or Ubuntu problem. Everything just freezes up with mouse and keyboard being totally unresponsive. Once in awhile hitting the Super Key the Force Quit option I put in my sidebar with fix things and unfreeze the screen. However for the most part I have to do a hard shutdown by hitting the PC power button to shutdown the PC and do a restart.

---

### Post by cruzer001 on 2018-03-24
My fix

Close the laptop lid (suspend) open it back up and the freeze is no longer present.

---

### Post by cruzer001 on 2018-03-24
I also run a Dell (precision/i7); bios is up to date.

---

### Post by cybrsaylr on 2018-03-24
> **cruzer001 said:**
> My fix

Close the laptop lid (suspend) open it back up and the freeze is no longer present.

Wish I could try that but my Dell i7 tower has no lid.

---

### Post by cruzer001 on 2018-03-24
> **cybrsaylr said:**
> Wish I could try that but my Dell i7 tower has no lid.
Not to mention its a crappy fix :)

---

