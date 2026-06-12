---
title: "ASUS K53SV notebook slow resume with 11.04"
date: 2011-05-30
forum: Hardware
---

### Post by fi2 on 2011-05-30
I installed 11.04 on a clean Asus K53SV notebook. All works fine, but after suspend, the time to resume takes over 1 minute. In this time the screen is blank, not even cursor, or pointer. The hard disk indicator flashes 9-10 secondly, then it starts to work, and that is when the user's login screen appears.

I tried the solution found [_here_]("http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010"), but no change.

Any idea would really be welcome.

---

### Post by lidex on 2011-05-30
1 minute is bad?
[http://ubuntuforums.org/showthread.php?t=1064894](http://ubuntuforums.org/showthread.php?t=1064894)

---

### Post by fi2 on 2011-05-31
> **lidex said:**
> 1 minute is bad?
[http://ubuntuforums.org/showthread.php?t=1064894](http://ubuntuforums.org/showthread.php?t=1064894)

Not if it is a switch on. But I am talking about resume from standby.

I had the feeling, that booting was faster, so I measured it:
resume from standby: 68 sec (at least it doesn't freeze)
boot-up from complete shutdown: 50 sec

Resume from standby is supposed to be something swift. Is it not?

---

### Post by lidex on 2011-05-31
I believe it has to do with how many programs are loaded. Generally, on a cold boot, no programs are loaded so it should boot quickly. 
Suspending is basically closing down your system in the exact state it's in so you can resume where you left off. I don't see how that would be inherently faster.

---

### Post by fi2 on 2011-06-01
No, no, this is not that. If I put this machine with Ubuntu 11.04 to standby with no application running at all, resume will still take the same minute. My Asus PC Eee with Ubuntu 10.10 does it it in less than 5 seconds with four desktops full of apps.

Is it not so that in standby mode the state of the system is in a snapshot (memory, and lately hd). The minute here is apparently spent on waiting for something, I just don't know what.

Off:
I must admit the whole matter starts to be a bit annoying with 11.04. I am really fond of Unity, but other than that there is a problem wherever I go: multitouch, virtual machine, video driver, compiz config, name it. I haven't spent this much time with typing in consoles for ages. This is not a system out of the box for sure.

---

### Post by fi2 on 2011-06-01
I found a solution [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1596545&highlight=Failed+access+USB+subsystem"), and it worked.

```
sudo apt-get install hibernate
```

---

### Post by fi2 on 2011-07-10
Well, I was a bit too hasty. Suspend stopped working after a few weeks. Now I am back to the same old problem: suspend is executed, but resume only starts after more than a minute. In this minute nothing happens, most of the time there is only a character mode console with a login prompt on the screen, but no keyboard input.

After something like 60-70 seconds a login window appears, and then it goes.

The strange bit is, that /var/log/pm-suspend.log shows the first entry after this minute.

I tried s2ram and settings in grub (just like [_[COLOR="Blue"]others[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1793274")), but nothing helps. The nasty bit is that sometimes it works, then just when you think you cracked it, it gives in again.

---

