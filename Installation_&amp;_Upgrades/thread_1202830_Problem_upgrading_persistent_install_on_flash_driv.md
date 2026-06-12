---
title: "Problem upgrading persistent install on flash drive"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by C.S.Cameron on 2009-07-02
I installed Ubuntu 8.09 to a four gig flash drive using usb-creator, it was working great. I am using separate home-rw and casper-rw partitions.
I reluctantly decided to upgrade to 9.04, so I deleted everything on the system partition and installed 9.04 using usb-creator again.
I modified my text.cfg file to make the new install persistent. When I booted everything looked ok, the desktop seemed just as I had left it however the Unlock Keyring box did not pop up.
I opened VirtualBox and tried to start XP, I got two error messages, "Failed to open a session for the virtual machine Windows XP" and "VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)".
On closer inspection I see that the network icon is missing from the top panel, as are the restart and shut down options. Also when I click Users and Groups I get a warning "The configuration could not be loaded", "You are not allowed to access the system configuration"
I would like to get this drive fixed, I have a second 4 gig flash drive with a full Ubuntu install on it however this does not leave enough room for much of a virtual machine.

---

### Post by quixote on 2009-07-03
Older versions of virtualbox needed to have the kernel module updated manually.  I thought there was an error message that said to reload the module, so if you're not getting that, this may not be the problem.  Still, it's worth trying:  ```
sudo /etc/init.d/vboxdrv setup
```
(That's from memory, so I hope I have it right.  If not, it won't do any harm, but it won't do any good either.)

Regarding the missing panel buttons:  9.04 has some silly ideas about separating what it thinks are user functions, like login, from system functions, like shutdown.  If you right-click on an empty part of the panel and select "add to panel" you can tell it to put the shutdown button back.  It may be the same problem with your network thingy.  That's officially part of "notification area" in "add to panel", and you can try to just add it back in and see if that solves the problem.

I'm not sure what to say about the Users & Groups problem.  Obviously, there's a permissions problem somewhere.  Hopefully, it's not too deepseated, and somebody else on the forum knows what to do.  I don't :(.

---

### Post by C.S.Cameron on 2009-07-05
Thanks quixote:
"sudo /etc/init.d/vboxdrv setup" got my vbox working again, found I had made a typo when I tried it earlier. Autocad, Rhino, SketchUp and Caesar are working as before.
Managed to get a shutdown icon onto the panel but have not found one to get my wireless working, nor have I found a way to get into Users and Groups

---

### Post by quixote on 2009-07-05
re wireless:  did you try to add "notification area" to the panel?  (There's nothing called "wireless" or "nm-applet", even though that's got to be what 100% of the people who need it are looking for.)

Glad the vbox is working.  One down.  :D

about the users problem:  just for the hell of it, try```
gksudo users-admin
```or```
sudo users-admin
```
"users-admin" is the name of the program you're running to access "Users and Groups".  If sudo lets you run it, but gksudo doesn't (which happens in some buggy situations) that might at least get us a starting point.  (You're supposed to use gksudo in these cases because of the way it handles paths, but sudo doesn't really hurt anything as far as I know.)

---

### Post by C.S.Cameron on 2009-07-09
I added notification area to the panel but still can't connect to the internet. 
I gave gksudo users-admin a try but still get the same error message

---

### Post by quixote on 2009-07-09
Did you try just plain "sudo users-admin"?  Same error message?  Can you run other sudo commands, or are they all off limits?  If sudo generally is unavailable, then it's a relatively simple matter of editing the sudoers file.  (I'd have to look it up.  vi sudoers, or something.)

For the wireless, can you access configurations by going to System> Preferences > Network Coonections ?  There's a long thread on command line [wireless configuration by wiemann01]("http://ubuntuforums.org/showthread.php?t=318539") that is very good that might help.

---

### Post by C.S.Cameron on 2009-07-15
I appologise for the delay.
sudo users-admin gives same.
Sudo other commands runs the command without asking for password.
System> Preferences > Network Connections is missing.
I think I deleted network manager thinking I could reinstall from the CD but I haven't been able to. Doing a new install using usb-creator would not even bring it back.

---

### Post by quixote on 2009-07-15
> Sudo other commands runs the command without asking for password.
This does NOT sound good.  The other stuff is an inconvenience, but this could be downright bad.  Have a look at your sudoers file.  An extensive how-to is [here]("https://help.ubuntu.com/community/Sudoers").  This is culled from there.

```
sudo visudo
```
That brings up your sudoers file for editing.  Don't make any mistakes.  This is a critical file and your computer won't boot if it's wrong.  (You could boot from a LiveCD and edit it, so don't panic, but do try to avoid typos.)  The commented lines have # in front of them.  The uncommented lines should look like this: > Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
If they don't, that's your problem and you should edit as necessary to bring it into line.  Especially note the line **# %sudo ALL=NOPASSWD: ALL **.  If that does not have the comment hash mark #, that is what is allowing you (as an ordinary user) to issue sudo commands without a password.

I think, I hope!, that if your sudoers file is straightened out, you'll find that the permission problem about users-admin also goes away.  This problem could be causing that.

---

### Post by C.S.Cameron on 2009-07-15
Had a look at my sudoers file
It's pretty much inline with what you suggest.

# User privilege specification
root ALL=(ALL) ALL

appears before 

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

and 

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL 

appears twice.

I'm thinking maybe some of the files created in casper-rw by 8.10 may not work with 9.04.
I'm thinking that if I delete everything in the casper-rw partition and keep everything in home-rw, it should be no worse than doing a fresh upgrade with a separate home partition. at least my virtual box should still be there.

---

### Post by quixote on 2009-07-15
Yes, your sudoers file looks fine.  Not sure how you'd get a duplicate entry, but I also don't think it should hurt anything.

> if I delete everything in the casper-rw partition and keep everything in home-rw
Hmm.  You're far beyond me in this.  Let us know how it goes if you go ahead with it.  As they're always saying, half the fun of Linux is (with apologies to the Wind in the Willows) messing about in the OS . . . simply messing about in the OS.  :D

---

