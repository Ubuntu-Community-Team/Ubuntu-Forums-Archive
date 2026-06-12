---
title: "New user - windows gone? Say it ain't so"
date: 2008-11-11
forum: General Help
---

### Post by cmoguer on 2008-11-11
Some one please help!
I've read so much about Ubuntu, decided to plug in an external drive to my laptop and give it a whirl. Problem is that it's my work laptop and I THOUGHT that it would install to the external drive - as I told it. 

It did - but the main boot off the main internal drive now always looks for that and never sees my main windows partition on the internal drive. 

I'm an MCSE and I know I did not tell it to blow the main partition away. All reference to install were to the external drive away but apparently, it's not as fool proof as I thought. 

Please tell me there is a way to restore my partition so the laptop boots as before -- pretty please? 

Thank you so much for any help

Manny

---

### Post by ju2wheels on 2008-11-11
If you are sure that you installed it to your external then it probably just blew away your MBR boot loader for Windows on your main drive (if you are lucky and did it correctly).

Try this: [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

---

### Post by ju2wheels on 2008-11-11
*Removed* double posted by accident

---

### Post by cmoguer on 2008-11-11
Thank you. I will try that. At the risk of sounding stupid .. I assume the LiveCD is the one I used to build the system right? Or is that something different? Also, it may sound simple but this is new to me - once I boot the CD, how do I get to the "terminal" screen or commands?
I really appreciate your help

---

### Post by stoneage on 2008-11-11
Yes, Live cd is the one you used to install.

Boot from the cd and use the first option, don't reinstall - but then you knew that.

Applications => Accessories => Terminal

---

### Post by ju2wheels on 2008-11-11
The LiveCD is the dekstop or dvd version of Ubuntu (If it let you preview Ubuntu before you installed it then you used the Live CD). 

If you boot into the Live CD then on the menu select Applications -> Accessories -> Terminal to get a command terminal.

---

### Post by cmoguer on 2008-11-11
Looks like it will be a lonng night :-(.

I got a "Couldn't find package ms-sys" message. I even did the system > admin > software sources  and checked the "universe repository". It updated a bunch of files but then still failed with the "Couldn't find package ms-sys" message after I issued the "install ms-sys" command as the other thread indicated.

Any ideas?

---

### Post by ju2wheels on 2008-11-11
For 64bit:

```

wget http://http.us.debian.org/debian/pool/main/m/ms-sys/ms-sys_2.1.0-1_amd64.deb

```

For 32bit:
```

wget http://http.us.debian.org/debian/pool/main/m/ms-sys/ms-sys_2.1.0-1_i386.deb

```

Then:
```

sudo apt-get install libc6 libgcc6
sudo dpkg -i ms-sys*

```

Edit: corrected libc to libc6

---

### Post by adult swim on 2008-11-11
it looks like this package hasnt been in the repos since gutsy.  you might want to give that version a whirl [http://packages.ubuntu.com/gutsy/ms-sys](http://packages.ubuntu.com/gutsy/ms-sys)

---

### Post by ju2wheels on 2008-11-11
Its not in the Intrepid repository, I would not go back to a gutsy package, use the debian version instead.

---

### Post by cmoguer on 2008-11-11
I didn't catch the subsequent replies in time. I tried the 1st suggested solution. Did not work. I loaded the XP CD, went to recovery console and plugged in FIXMBR. That didn't work - now it says invalid partition. I give up - I will bring it in to work and confess my crimes. 

I will say that it's (installation) not as fool proof as it claims. This never should have happened without a warning. I should have known better but I guess I haven't learned yet. Thanks for all your help.

---

### Post by TeXtonyx on 2008-11-11
Did you also run fixboot from Recovery Console.

The other thing to try is use TestDisk to rebuild the boot sector
from the XP backup.

---

