---
title: "video troubleshooting in Intrepid vs Hardy and previous"
date: 2008-11-27
forum: Hardware
---

### Post by doas777 on 2008-11-27
ok, so I'm getting used to Intrepid, and for the most part I like it, but since X no longer relies on a well configured xorf.conf anymore, I'm finding that a lot of the old approaches to troubleshooting and fixing vid card and monitor problems (when they do arise), just don't work well anymore. 

So now that the xorg.conf is not configured, is the video configuration information stored? if so how do we edit it?  

if you were helping someone on the forums, how would you determine if they had a restricted driver installed, or what their current res/refresh/monitor dimensions are? xorg.0.log?

should 'dpkg-reconfigure xserver-xorg' still work? 

if you configure and write your xorg with a tool like nvidia-settings, does it override the auto-generated config info? 

on one nvidia box I also had to set the gnome-display-properties to the same value as nvidia-settings before it would work. otherwise the control panel seemed to have overrode the nvidia and xorg settings. is that common, and if so, where does gnome-display-properties store the user-configured resolution?  

Thanks,
franklin

---

### Post by doas777 on 2008-11-29
bump, bumpity, bump bump ... bump bump

---

### Post by cragged on 2008-12-01
I could use answers to these questions too. Screen res at first boot was fine under Intrepid, but has since gone to 1024x768 when should be 1280x800.

The driver for BCM4312 wireless is not automatic either...but that is another question.

---

### Post by doas777 on 2008-12-07
At this point i have to assume that this thread being snubbed as someone has to have figured out most of the answers to these issues, so I guess, never mind.

---

### Post by nowhere@cox.net on 2008-12-08
That would be a shame because I too am having troubles with this new methodology. My X wouldn't start at all after upgrade. When I drop to console mode, the text is huge and doesn't fit on the screen so I cannot run dpkg-reconfigure xserver-org since I can only see the top left corner of the blue dialogs. I was able to rename the xorg.conf file that was left after update by issuing a command then typing clear each time. This at least got me to gdm login screen but after logging in X would not start again.

I ctrl-alt-F1 to enter console mode but it is still with huge text. I ran dpkg-reconfigure -phigh xserver-org which I guess doesn't have any interaction and after reboot I was finally able to get past the log in but only with very low resolution and a terrible refresh rate. Restricted package manager shows no drivers (should have an nvidia one). I tried to reset the resolution using the tool on the preferences menu but then my monitor wouldn't accept the refresh rate and I couldn't use X again. dpkg-reconfigure xserver-org didn't do anything and neither did dpkg-reconfigure -phigh xserver-org. Never offered to change resolution or monitor refresh rate. 

I finally used the safe terminal session from gdm to get a terminal window from which I could manually launch gnome-display-settings to revert the settings. From some reason this tool thinks there are two displays which there are not.  So I am back to being able to log in with low res and low refresh flickering at me. I am doing a complete apt-get upgrade with the new -10 kernel and all 215MB of other stuff. We will see what happens after that. It would be nice if I could find out where the config stuff is so that I can manually fix it when the auto stuff doesn't work...

---

### Post by lswb on 2008-12-08
> **doas777 said:**
> At this point i have to assume that this thread being snubbed as someone has to have figured out most of the answers to these issues, so I guess, never mind.

I don't think so, when it comes to xorg, it is quite possible that no one really knows! :)

I see that despite all the changes to X over the last several months, the FAQ on the xorg foundation web site is still dated May of this year. I know that there are lots of questions about the new minimal xorg.conf file but I haven't seen many answers yet.

It would be great if all the major distributions like RH/fedora, ubuntu, debian, etc. would get together and do something about the state of documentation for X, considering how dependent they all are on X working properly.

---

### Post by doas777 on 2008-12-08
Nowhere, it sounds like your VGA mode may be off (since non-X screens are displaying funny). you might wanna try setting it manually in your grub config (or with startup-manager). otherwise, your guess is as good as mine. Good luck!

---

### Post by doas777 on 2008-12-08
> **lswb said:**
> I don't think so, when it comes to xorg, it is quite possible that no one really knows! :)

I see that despite all the changes to X over the last several months, the FAQ on the xorg foundation web site is still dated May of this year. I know that there are lots of questions about the new minimal xorg.conf file but I haven't seen many answers yet.

It would be great if all the major distributions like RH/fedora, ubuntu, debian, etc. would get together and do something about the state of documentation for X, considering how dependent they all are on X working properly.

that is a good point, I guess i was assuming the uber-geniuses were laughing at my n00bitude. To The Community, I apologize if i have maligned you unjustly. lol. 

regardless, your right, the documentation is in a poor state. I'm shamed to say it, as I'm working on 'agile' projects lately. I wish I had a box to experiment on, but all mine are stable at the moment, so i don't wanna mess with 'em too much right now.

anyway, thanks, at least i feel better about it.
Franklin

---

