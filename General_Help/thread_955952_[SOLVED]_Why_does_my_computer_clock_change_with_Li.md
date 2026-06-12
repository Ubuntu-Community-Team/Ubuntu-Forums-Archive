---
title: "[SOLVED] Why does my computer clock change with Linux?"
date: 2008-10-22
forum: General Help
---

### Post by Davy-D on 2008-10-22
Hi,
First post, new member, so sorry if this has been answered before.
When I change over from Ubuntu to Windows my pc clock changes by 1 hour.
I have set both operating systems to Greenwich Mean Time - London + daylight saving time (BST) but when I change back from Ubuntu to Windows my time has altered back one hour to GMT...???
Does anybody know what I am missing please?
Davy-D.

---

### Post by taladan on 2008-10-22
sounds like you probably need to run windows updates.  If it's an old copy of windows that isn't patched all the way up, it may have an effect on that.


Something to check in to

Tal

---

### Post by Kralizec on 2008-10-22
Additionally, you may wish to try syncing your hardware clock with your system clock from within Ubuntu.
```
sudo hwclock --systohc
```

---

### Post by bdeb on 2008-10-23
I think you should open your window time and date settings and  make sure under the time zone tab that the box is ticked for daylight savings.

---

### Post by Rocktman2 on 2008-10-23
If you want the absolute correct time when in Window$, try D4Time. [http://www.thinkman.com/dimension4/download.htm/](http://www.thinkman.com/dimension4/download.htm/).

You can choose one of the U.S. Naval Observatory time clocks or you can pick from a long list of other time servers around the world, if you so desire.

When you boot into Window$, D4Time will update your Window$ clock to the correct time, provided your time zone is set correctly in Window$.

I've been using it for years & can recommend it w/o reservation. Just my 2 cents.

---

### Post by Nepherte on 2008-10-23
Windows only stores the local time on the bios battery. Linux can do both local and GMT. When you tell linux to save  GTM time, the time will be different on Windows as it thinks its the local time.

---

### Post by Davy-D on 2008-10-23
Thank you all for your suggestions. Both Ubuntu & Windows are fully up to date. Both have my time set for London Greenwich BST (Daylight Saving Time for US citizens). I have synced my hardware clock with my system clock and set my time servers.
Now here's the strange thing: I have 3 HDD's; one with Windows; one with Ubuntu & one with Fedora. But when I boot from Fedora to Windows my Windows clock does NOT change.
But when I boot from Ubuntu to Windows it DOES; by one hour back..??

Now at first I thought it might be either Windows OR Ubuntu: but since it ONLY does it FROM Ubuntu I asked the question here in case anyone else had found the same problem..?? If no one else has found the same problem, I will have to ask it on a Windows XP forum.
Davy-D.

---

### Post by estyles on 2008-10-23
In the Ubuntu time settings, you should be able to tell it to use local time (I think there's a box that says "use UTC" which you have to uncheck).  Ubuntu likes to set your system clock to UTC and then display local time.  Windows just reads the system clock and assumes it is local time.  If you tell Ubuntu not to do that, it will just set the system clock and read it as is.

---

### Post by Davy-D on 2008-10-23
Thank you estyles from your reply I found this post from a couple of years ago:-

Ubuntu assumes that your hardware clock is set to UTC (Universal Time Coordinated).
Windows assumes that your hardware clock is set to local time.
Naturally, we're "right", but as there's apparently no way to configure Windows to use UTC for the hardware clock, you can instead configure Ubuntu to use local time for the hardware clock by modifying "/etc/default/rcS".
----
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes

Now my knowledge of Ubuntu is very limited to say the least and I don't seem to have the right permissions to change UTC.
Could somebody type out longhand what I have to say in my Terminal commands please..?? 
Thanks,
Davy-D.

---

### Post by _sAm_ on 2008-10-23
Davy; normal users cant change the system on Ubuntu, only root. You can "become" root in the terminal with adding "sudo" in front of the command. 

So type(or paste):
```
sudo gedit /etc/default/rcS 
```

Enter your password when asked. 

Change; the yes to no for UTC
Press save and close.

(Learn more about sudo here; [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo))

---

### Post by Davy-D on 2008-10-23
Well now sAm: I thank you for that. You are hereby promoted to top of the class and can hand the pencils out. [I can think of no higher award at this time of night 23.38]
Davy-D. :)

---

