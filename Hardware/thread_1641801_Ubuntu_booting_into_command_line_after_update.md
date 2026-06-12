---
title: "Ubuntu booting into command line after update"
date: 2010-12-09
forum: Hardware
---

### Post by donde on 2010-12-09
Hello all.  I am a total noob when it comes to Ubuntu (or anything Linux).  Last night I turned on my netbook (original Dell Mini 10) as I always do and Ubuntu loaded up to the GUI like normal.  As I was doing my thing, the Update Manager popped up and I installed all the updates it listed (I don't remember what they were unfortunately).  After the update was done, I restarted my system and it then started booting into the command line directly.

I have no idea what I should do from this point forth.  I tried to look up some help but most of what I come across, I can't make head nor tales of.  So any help would be appreciated.  Thanks in advance.

FYI, I am using the latest Ubuntu Netbook version on a Dell Inspiron Mini 10.

---

### Post by sikander3786 on 2010-12-09
Welcome to the forums :-)

Try these commands.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

It might throw an error like file not found. Ignore it and proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

Post back any errors encountered there.

If it still doesn't boot to the GUI, post the output of this one as well.

```
lspci | grep VGA
```

---

### Post by donde on 2010-12-10
> **sikander3786 said:**
> Welcome to the forums :-)

Try these commands.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```It might throw an error like file not found. Ignore it and proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
``````
sudo shutdown -r now
```Post back any errors encountered there.

If it still doesn't boot to the GUI, post the output of this one as well.

```
lspci | grep VGA
```

Ok, I entered the commands like you said and eventually the netbook restarted. Thing is, it went right to the command line again.  I thought that I maybe entered in a command wrong so I re-entered the commands again.  When the netbook restarted the second time around, now it seems as if it's loading up fine but then the screen goes black and that's it.  Totally at a loss.  Help.

---

### Post by sikander3786 on 2010-12-10
Press and hold down Shift key from Bios screen until Grub menu pops up. Highlighting the first entry in Grub menu, press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. See if you can see the desktop now.

---

### Post by sr14 on 2010-12-10
Hello,

Try re-installing your VGA card from a live cd. A similar thing I happened before an update.

---

