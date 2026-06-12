---
title: "Seek Help with Graphics Issue Toshiba Satellite"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by ktritty on 2009-06-06
I am helping a friend who had bootlegged XP (which I had discouraged) on a Toshiba Satellite Laptop.  It got pretty well shredded by at least one virus, and I talked her into letting me put Ubuntu on it after considering a few options.

The only problem I am having, is that nothing graphical will work (not even the installer!).

Ubuntu Server installs and works fine (text command line only).

I tried the alternate installer for Ubuntu, and it works fine.  But it will not boot, it hangs where GNOME normally kicks in.  I tried recovery boot, checked file system, attempted the autofix graphics problem utility.

The system runs perfectly in command line mode, but still hangs for normal boot or when "startx" command is issued.

I have no idea what version of Toshiba Satellite this is, nor much about hardware, etc as I don't know commands for identifying this type of stuff yet.  I have network connection working.  I am looking for someone who can help me troubleshoot what is likely a graphics problem and get GNOME running.

A good start might be to help me learn how to identify the model/version of this laptop and how to identify the hardware and CPU/memory/disk and other basics.

Thanks!

---

### Post by ktritty on 2009-06-07
I solved this for now by installing windows XP, I had a genuine copy lying around unused.  The installer ran perfectly on the first try.

I don't like this solution, but I had to have the computer back to her by monday (june 8th 2009).

I am open for input still on getting the ubuntu graphics not to freeze, as I don't think windows xp will be a good long-term answer for her.

---

### Post by Topsiho on 2009-06-07
This won't help you much, only thing is that Ubuntu runs nicely on my Toshiba Satellite A50 notebook. Which doesn't mean it will run on every Satellite of course.

Looks like Ubuntu doesn't recognize the graphics card in the Satellite of your friends. I think that that chance is the main problem with computers of the so called A-brands such as Toshiba or HP or so: that they do not always use the generally available hardware, but their own versions.

Topsiho

---

### Post by siabost on 2009-06-10
ktritty,

Re your laptop problem:

I had a problem similar to yours booting Debian on an Easynote laptop. This may be worth a try, it worked for me -

After installing (K)ubuntu 9.04 with the Alternate Installer CD: 
1. Boot in recovery mode
2. Drop into a shell (command line)
3. TYPE:

```
sudo nano /etc/default/acpi-support
```

4. Enter your password when prompted.
5. CHANGE:

```
SAVE_VBE_STATE=TRUE
```

to

```
SAVE_VBE_STATE=FALSE
```

6. Press "Ctrl+O" then "Return" to save.
7. Reboot.

Original thread for this solution can be found at [https://lists.ubuntu.com/archives/ub...il/017581.html](https://lists.ubuntu.com/archives/ub...il/017581.html)

Just tried the above on my Dell Desktop (problematic booting) & Jaunty booted correctly!!

Best of luck.

---

