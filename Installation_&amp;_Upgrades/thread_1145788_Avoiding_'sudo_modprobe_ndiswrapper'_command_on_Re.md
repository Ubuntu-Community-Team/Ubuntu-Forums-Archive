---
title: "Avoiding 'sudo modprobe ndiswrapper' command on Reboot (How can I?)"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by wklang on 2009-05-02
I recently upgraded from 8.10 to 9.04 and - using the instructions contained in the thread

"http:////ubuntuforums.org/showthread.php?t=530772"

I was able to get my WUSB300N wireless adapter to run......until I reboot the machine.

On reboot, I have to once again issue the command in order to restart th wireless adapter.

```
sudo modprobe ndiswrapper
```

I boot Ubuntu into the Gnome Display.  Is there an "rc" file of some sort where I can insert this command where it'll automatically be executed when I login?

---

### Post by amingv on 2009-05-02
Just do

```
sudo ndiswrapper -m
```

```

```

---

### Post by wklang on 2009-05-02
Thanks, but I tried it under 9.04 and - while it worked under 8.10, it doesn't appear to work under 9.04.

What I get when I try is this:

```

wes@kashgar-ubuntu:~$ sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

wes@kashgar-ubuntu:~$

```

Any suggestions?

---

### Post by amingv on 2009-05-02
Try:

```
sudo su
echo "ndiswrapper" >> /etc/modules
exit

```

---

### Post by wklang on 2009-05-02
Thanks, amingv. The fix you suggested worked like a charm!

---

### Post by mirrorx on 2011-08-03
> **wklang said:**
> I recently upgraded from 8.10 to 9.04 and - using the instructions contained in the thread

"http:////ubuntuforums.org/showthread.php?t=530772"

I was able to get my WUSB300N wireless adapter to run......until I reboot the machine.

On reboot, I have to once again issue the command in order to restart th wireless adapter.

```
sudo modprobe ndiswrapper
```

I boot Ubuntu into the Gnome Display.  Is there an "rc" file of some sort where I can insert this command where it'll automatically be executed when I login?
Its telling file not found,

and when I tried to download and install ndiswrapper,I am getting make error [2]

what to do ?

---

