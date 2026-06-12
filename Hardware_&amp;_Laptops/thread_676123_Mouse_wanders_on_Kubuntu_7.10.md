---
title: "Mouse wanders on Kubuntu 7.10"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by ktomazin on 2008-01-23
Hi, I have a Dell Inspiron 8500 and am running Gutsy (Kubuntu 7.10) and recently my mouse has started wandering about the screen especially when I type.  Typically it heads off for either the bottom left corner of the screen or the top right corner.  Has anyone seen this or have any ideas as to how I might go about debugging it?  Its driving me crazy. 

A couple other data points that may be relevant: (a) I recently started using a docking station and (b) I switched from a wired MS mouse to a wireless MS mouse, but the problem still exists after I switch back to the original configuration (no docking station and the wireed mouse).

Thanks in advance to anyone who might help me in debugging this.

---

### Post by jeffus_il on 2008-01-23
A Guess, Try disable the touchpad.

---

### Post by t20racerman on 2008-01-23
I had the same on an old Dell laptop - the touchpad was faulty. I bought a trashed laptop of the same type cheap on eBay and swapped the touchpad over. Problem solved!

Hope this helps.

---

### Post by ktomazin on 2008-01-23
How do I disable the touchpad?  Just remove that entry from xorg.conf file?

---

### Post by jeffus_il on 2008-01-23
I have a synaptics touchpad and the is a utility which can disable it.

called gsynaptics (package)

---

### Post by ktomazin on 2008-01-23
I tried to remove the entry from the xorg.conf file and that didn't work (couldn't restart X), so where do I get the utility?

Also, I really don't use the touchpad, so it doesn't seem likely to me, but I'll try anything at this point.

---

### Post by ktomazin on 2008-01-23
How do I disable it?

---

### Post by t20racerman on 2008-01-23
The best way is to undo the laptop case and unplug the connector.

---

### Post by ktomazin on 2008-01-23
sorry, I didn't originally see that you gave me the name of he package.

Anyway, I installed it, disabled the touch pad and am still seeing the same behaviour.  Especially when I type into a window - the mouse travels towards the lower left hand corner of the screen and stays there once it gets there. 

Any other ideas?

---

### Post by jeffus_il on 2008-01-23
Is the machine a dual boot with windows? can you test it with windows? if not, with the livecd?

---

### Post by t20racerman on 2008-01-23
Sorry to repeat my earlier comment about removing the connector, but I tried all kinds of software disabling and couldn't get it work.  Pulling the plug worked though! :-)

---

### Post by ktomazin on 2008-01-23
Could it be the eraser head cursor control in the middle of my keyboard instead?  Does anyone know how to disable that?

---

### Post by jeffus_il on 2008-01-23
Maybe disconnecting the plug as t20racerman suggests is an option, would you like to try it? It seems as though he had the same problem, I don't know your machine.

---

### Post by ktomazin on 2008-01-23
Yes, I would like to try it.  I just attempted, but apparently removed the wrong connect because the touchpad still worked when I rebooted.  Does anyone out there know where I can find the device?  Do I have remove the entire bottom of the computer?  There are a number of little panels but I didn't see it under any of them.  Thanks again.

---

### Post by ktomazin on 2008-01-23
Thanks for the suggestion ... unplugging the touch pad fixed the problem.  Just for the benefit for anyone else who may encounter this problem in the future, don't be foolish and think that you can get at the cable by unscrewing every screw on the bottom of the computer like I did ... to get at the cable you have to remove the keyboard.  I followed the instructions here: [http://support.dell.com/support/edocs/systems/ins8500/en/8500/sm/keyboard.htm](http://support.dell.com/support/edocs/systems/ins8500/en/8500/sm/keyboard.htm)

The touchpad connector is just adjacent to the keyboard connector.

Thanks again to everyone for your help.  I can finally get back to work :-)

---

### Post by t20racerman on 2008-01-23
It was the only way I could stop it too!  Glad my suggestion helped. :)

---

