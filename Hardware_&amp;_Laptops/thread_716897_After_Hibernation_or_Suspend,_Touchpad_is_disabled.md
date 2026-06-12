---
title: "After Hibernation or Suspend, Touchpad is disabled (ceases to function)?"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by newagelink on 2008-03-06
[COLOR="Indigo"]I have had this issue since Ubuntu 7.04, and sadly the upgrade to Ubuntu 7.10 hasn't fixed it.

Basically, my touchpad works *before* I put the computer into suspend or hibernation, but upon return it ceases to function. I don't know if it's being disabled, or if a configuration file is messing up; I don't know where to look, either; I can't understand anything the Device Manager ("Hardware Information") says: it lists so many foreign things, like "82801 Mobile Bridge", "OSS Sequencer Device" (two of them), ...

I've gotten an external USB mouse (because my left-click on my Gateway laptop broke after three weeks and the touchpad doesn't work properly in Windows), so I can ignore the issue, but it's annoying that I must always restart my computer if I wish to use the touchpad.

Any ideas? Thanks for reading. It's kind of funny, though, that the touchpad works better in Ubuntu than Windows XP -- with a "Designed for Microsoft Windows XP" sticker on this gateway laptop ... I try to configure tap zones in Windows, and upon restart the configuration settings are lost. I guess that's why I've not used Windows in forever. :)[/COLOR]

---

### Post by musashi140 on 2008-03-20
any help on this issue would be great, as i suffer from the same issue on my gateway CX 2610

cheers.

mike

---

### Post by akshaysrinivasan on 2008-05-02
Restarting gdm manually gets the touchpad to work normally again.Hope that helps.

> sudo /etc/init.d/gdm restart

P.S- You'll lose your X session.

---

### Post by newagelink on 2008-05-25
**[COLOR="Red"]Is there a way I can stop Ubuntu Forums from stripping quoted code/quotations?![/COLOR]** > **akshaysrinivasan said:**
> Restarting gdm manually gets the touchpad to work normally again.Hope that helps.

[the command to do it]

P.S- You'll lose your X session.[COLOR="Indigo"]Isn't that the same as Ctrl+Alt+Backspace, logging me out? (As you said, "losing your session.") Or does that command restart it, while the shortcut simply kills it, hoping it'll automatically restart?[/COLOR]

---

### Post by 52vincent on 2008-07-20
OK I would like to revive this Dead thread, because I recently installed Ubuntu and have the same issue.
If I leave the computer on and idle for a while after the screen saver times out and it goes into hibernation or suspend I cannnot revive it with the touchpad. the screen seems to brighten slightly but that is it no pointer on the blank screen. I have to restart to get  it back.
iam reviving this thread cause I already searched for other answers and found none this was the closest, but unfortunately no advice given yet.

Thanks in advance for the help

---

