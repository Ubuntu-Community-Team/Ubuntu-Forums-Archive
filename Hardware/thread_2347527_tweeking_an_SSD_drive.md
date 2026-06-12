---
title: "tweeking an SSD drive"
date: 2016-12-26
forum: Hardware
---

### Post by Jack_Shankle on 2016-12-26
Thank you for Ubuntu-Mate
Stats: Mate 1.12.1,  Ubuntu 16.04.1
          Kingston SSD

Please respond at the novice level. I
know just enough about Ubuntu to be dangerous.
SSDs need tweaking from time to time.
How does one do this on Ubuntu?

---

### Post by oldfred on 2016-12-26
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

All I do is change fstab to use noatime and turn off Ubuntu's weekly trim and add my own daily trim. Note that then old data is erased daily so recovery is then not possible. If new valuable data written to SSD back up immediately. I normally just have operating system on SSD, so I do not back that up, but would reinstall if major issues.

 Shows both discard (not recommended) & fstrim methods for trim and script with log
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
sudo nano /etc/cron.daily/trimSSD
sudo chmod +x /etc/cron.daily/trimSSD


 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

---

### Post by Jack_Shankle on 2016-12-26
Thank you for responding OldFred.
I realize the info you gave will work BUT I have an
Ubuntu learning curve that is at the novice level.
Ex: Fstrim - where is it, how to access terminal,
 where do I exec the Sudo commands etc?

Guess what I really need is a program that will handle
 tweaking the SSD in Ubuntu by asking me questions
on what I want to do. Anything else is just to complicated for me.

---

### Post by oldfred on 2016-12-26
Terminal is not really difficult. 
I almost always copy & paste, but I have saved a lot of commands into text files.
Only a very few I use a lot do I remember (perhaps something about the old in oldfred?)

Some resources on command line are in the sticky thread at top of New to Ubuntu.
[https://ubuntuforums.org/forumdisplay.php?f=326](https://ubuntuforums.org/forumdisplay.php?f=326)
And then the wiki:
[https://help.ubuntu.com/community/Links?action=show&redirect=CommandLineResources](https://help.ubuntu.com/community/Links?action=show&redirect=CommandLineResources)

With Ubuntu you have to preface system command with sudo and enter your password.
And you can copy & paste into terminal with mouse, right click choose paste. 
Or control-shift-v to paste.

nano is an old style text editor. You have to manually move cursor to correct location with arrow keys and then you can paste or type.

---

### Post by Jack_Shankle on 2016-12-27
Thank you for helping OldFred.
I tried sudo mv-v/etc/cron.weekly/fstrim/etc/cron.daily
All I got was "command not found".

I can't even figure out how to get into "terminal".
I tried caja then open terminal and that didn't work.

Is there a difference between Mate terminal and Terminal?

I did read the items you suggested previously. They didn't help
 me with this problem. Sorry for my ignorance.

---

### Post by oldfred on 2016-12-27
Part of the reason we use terminal is there are many flavors, and each has a different gui. Or tying to explain how to use mouse is just about impossible.
 [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE & new in 17.04 Ubuntu Budgie 

But to get to terminal:
See section on how to invoke terminal
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

Usually alt-f2 (both keys at once)opens a small terminal window
Or control-alt-t (all 3 keys) Full screen or part screen terminal.

I find terminal in menu and drag that to desktop to create icon, but I am using Ubuntu with fallback which is somewhat like gnome, but slightly different version.

I did not post a mv command. But spaces are vital in terminal. Adding or deleting a space can totally change a command. And some on line wordpress sites do not show spaces well as kerned so space is less, they also often show two - as one longer one.

---

### Post by slickymaster on 2016-12-27
*Thread moved to **Hardware**.*

---

### Post by Jack_Shankle on 2016-12-27
Thank you for helping OldFred.
I tried these two items in terminal.
sudo mv -v/etc/cron.weekly/fstrim/etc/cron.daily
I tried it without the space between mv -v.
Neither worked.

I also tried: sudo fstrim-v/ in terminal
It didn't work either.

With "man" I looked at fstrim and mv. This didn't solve my problem.

---

### Post by oldfred on 2016-12-27
You have to have spaces between command and parameter and from & to paths.

I just manually create a new fstrim in daily with the command I posted above and copy & pasted the commands in the linked blog/article. I turn off execute bit on weekly and turn on execute bit on my new file.

This would be more correct, but I have not tested it.
sudo mv -v /etc/cron.weekly/fstrim /etc/cron.daily

---

### Post by Jack_Shankle on 2016-12-28
Thanks again for your patience with me.
I don't understand your previous message.

What is daily?
What is the command posted above?
My sudo command looks the same as yours.
It does not work.

---

### Post by oldfred on 2016-12-28
Daily was referring to cron.daily.

Shows both discard (not recommended) & fstrim methods for trim and script with log
[http://www.webupd8.org/2013/01/enabl...te-drives.html](http://www.webupd8.org/2013/01/enabl...te-drives.html)
I copy commands from above blog into new trimSSD file. Nano is editor. chmod with the +x adds execute bit so it can run.
sudo nano /etc/cron.daily/trimSSD
sudo chmod +x /etc/cron.daily/trimSSD

mine with space before each path
sudo mv -v /etc/cron.weekly/fstrim /etc/cron.daily                 
Yours with no space before from /etc... and to /etc...
sudo mv -v/etc/cron.weekly/fstrim/etc/cron.daily

---

### Post by Jack_Shankle on 2016-12-28
Thank you again OldFred,
That seemed to work. Those spaces are hard to see in
the documentation. I usually insert a "b" with a slash through it
in any documentation I do.

---

