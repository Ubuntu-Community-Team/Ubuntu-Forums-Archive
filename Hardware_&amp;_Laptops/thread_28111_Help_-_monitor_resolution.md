---
title: "Help - monitor resolution"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by chickengirl on 2005-04-18
I just installed Hoary and I'm having a problem with my monitor -- I'm only getting 640x480 resolution and I can't find any way to increase it. I tried system > preferences > screen resolution, but it won't let me increase it above 640x480.

All the relevant information I can think of:
*I usually use 1078xwhatever it is, and I know that windows will let me use at least 2 resolutions higher than that.

*This is an emachines monitor, it came with my computer ~3 years ago.

*The sticker on the front of the CPU says: 3D Intel Extreme Graphics -- Intel 845GL chipset

*Mandrake 10.1 detected it just fine when I had it installed.

Help would be *greatly* appreciated, I'm getting claustrophobic!

---

### Post by chickengirl on 2005-04-18
Just noticed something else -- my internet connection, um, sucks. I can use firefox just fine, but xchat can't connect to any servers, gaim can't sign in to any of my accounts, firefox's missing plugin search can't connect to wherever it's trying to connect to (I tried to go to a site that needs java). I can't find any network/internet settings that are preventing me from accessing the internet in any way.

---

### Post by mohaham on 2005-04-18
Hi..
you might want to read this thread to resolve the monitor resolution problem..
[http://www.ubuntuforums.org/showthread.php?t=21984&highlight=monitor+1280x800](http://www.ubuntuforums.org/showthread.php?t=21984&highlight=monitor+1280x800)

---

### Post by chickengirl on 2005-04-18
[QUOTE=mohaham]Hi..
you might want to read this thread to resolve the monitor resolution problem..
[http://www.ubuntuforums.org/showthread.php?t=21984&highlight=monitor+1280x800](http://www.ubuntuforums.org/showthread.php?t=21984&highlight=monitor+1280x800)[/QUOTE]
 I tried to edit my xorg.conf the way it said to in the OP of that thread...... but all of the relevant entries are already there. And I'm still in 640x480 HELL.

---

### Post by chickengirl on 2005-04-18
I can't seem to connect to any protocol other than HTML. FTP don't work. Xchat don't work. Gaim don't work.

Does this happen to everyone, or did I just get the Installation From Hell?

Why did I leave Mandrake again? Oh yeah, I was under the impression that Ubuntu was better or something. What the **** was I thinking??

---

### Post by locutus24 on 2005-04-19
If you have knoppix, boot that up and if it will most likely run 1024x768 at which point you should be able to copy the XF86Config file to a floppy. Then load it into the hoary machine, chang XF86Config over to xorg.conf :w! this will work only if you have a way to copy the XF86Config file.
Trust me i was a former mdk 10.1 user, im enjoying ubuntu quite marrily
For the internet log into root account, and go to "Networking" deactive your connection then reactivate this cleans up the ip address

---

### Post by chickengirl on 2005-04-19
I deleted Ubuntu and ran screaming back to Mandrake.

Now, honestly, I'm a little confused. All the reviews I read before downloading Ubuntu said that it "just worked" and that it was good at detecting hardware.

Uh, what were they smoking?

If I have to be running all over the internet trying to download drivers and edit my config files by hand JUST so that I can get my 3 YEAR OLD monitor/video card working right, we have a problem.

This is not "Linux for human beings". This is "Linux for ultra-l33t haxx0rs who consider it a badge of honor that they had to spend 6 hours getting their basic hardware up and running after a linux installation".

I know I'm sounding a bit caustic right now. I'm just so incredibly disappointed. I really thought that ubuntu was going to be really f*cking cool. :(

---

### Post by laka on 2005-04-19
Ubuntu is, as you say, fucking cool, and I can't see why it didn't work for you. It aint much you can mess up in the installation.. did you type in right nameserver, so everything got installed right?

What kind of connection do you have? 56k modem? ;-P

---

### Post by chickengirl on 2005-04-19
[QUOTE=laka]What kind of connection do you have? 56k modem? ;-P[/QUOTE]

I'm on a college LAN. It's Ubuntu's fault that it got messed up. Now it doesn't work in Mandrake either.

---

### Post by Spud on 2005-04-20
[QUOTE=chickengirl]I'm on a college LAN. It's Ubuntu's fault that it got messed up. Now it doesn't work in Mandrake either.[/QUOTE]
[FONT=Tahoma]Haha if Mandrake won't work either then it's not Ubuntu's that's the problem then, it's your PC. Mandrake prolly installed generic monitor drivers and let you choose higher resolutions than the monitor itself recommends (can be dangerous for monitor).

If your on a college LAN you most likely tried out your browsing in FireFox at a busy time? This is my first post here and I only just installed Ubuntu today and already this craps all over Mandrake in user friendlyness.

Go back to Mandrake and stop blaming the OS for all your PC problems if your gonna be like that.[/FONT]

---

### Post by chickengirl on 2005-04-20
[QUOTE=Spud]Haha if Mandrake won't work either then it's not Ubuntu's that's the problem then, it's your PC.[/QUOTE]

I eventually did find out what the problem was with mandrake, it was my firewall settings. That doesn't explain what was wrong with ubuntu though.

> Mandrake prolly installed generic monitor drivers and let you choose higher resolutions than the monitor itself recommends (can be dangerous for monitor).

I have had this monitor and this video card for over 3 years and it has always been at 1024x768 and I have not *ever* had even one problem with it, in windows or in mandrake. Mandrake detected my video card. Ubuntu did not even bother to try.

> This is my first post here and I only just installed Ubuntu today and already this craps all over Mandrake in user friendlyness.

Obviously one of us got our copy of Ubuntu from an alternate universe.

---

