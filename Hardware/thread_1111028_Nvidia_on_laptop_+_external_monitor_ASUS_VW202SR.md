---
title: "Nvidia on laptop + external monitor ASUS VW202SR"
date: 2009-03-30
forum: Hardware
---

### Post by don_eros on 2009-03-30
Hi everyone,

I have a Toshiba Satellite A100 317, I've always been using an external monitor with it (Dell 19''), recently I upgraded to a 20'' ASUS VW202SR but I haven't been able to get the optimal resolution (1680x1050), 1280x1024 worked with the old monitor and still works with the new one, but it's really less than ideal.

I've obviously tried using the "NVIDIA X server settings" applet, but the resolution I need (1680x1050) isn't listed. I tried setting it manually in xorg.conf but when I restart X I get no signal. I tried everything I could find when googling for various combinations of the involved keywords.

I even upgraded to Jaunty beta today to see if anything had changed with the new distro but I get the same problem (BTW smoothest upgrade ever! =D>).

Does anyone know of anything else I could try? I remember reading somewhere that nvidia-settings was broken in Intrepid, any news on that front?

Here's the configuration:

- Toshiba Satellite A100 317
- monitor: ASUS VW202SR
- VGA: GeForce Go 7300

lspci actually gives me this:

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

Thanks for your patience,
de

---

### Post by skotos on 2009-03-30
> **don_eros said:**
> Hi everyone,

I have a Toshiba Satellite A100 317, I've always been using an external monitor with it (Dell 19''), recently I upgraded to a 20'' ASUS VW202SR but I haven't been able to get the optimal resolution (1680x1050), 1280x1024 worked with the old monitor and still works with the new one, but it's really less than ideal.

I've obviously tried using the "NVIDIA X server settings" applet, but the resolution I need (1680x1050) isn't listed. I tried setting it manually in xorg.conf but when I restart X I get no signal. I tried everything I could find when googling for various combinations of the involved keywords.

I even upgraded to Jaunty beta today to see if anything had changed with the new distro but I get the same problem (BTW smoothest upgrade ever! =D>).

Does anyone know of anything else I could try? I remember reading somewhere that nvidia-settings was broken in Intrepid, any news on that front?

Here's the configuration:

- Toshiba Satellite A100 317
- monitor: ASUS VW202SR
- VGA: GeForce Go 7300

lspci actually gives me this:

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

Thanks for your patience,
deWell, I have always successfully solved my Nvidia configuration settings by running the ENVY package that is now in the repositories starting from 8.10.
Furthermore, I have noticed that the Nvidia drivers are not able to correctly update the *xorg.conf* file because *nvidia-settings* is run by the user you are currently logged in with.
My solution to have *nvidia-settings* running fine was to correct the startup command like this```
gksu /usr/bin/nvidia-settings
```FYI As soon as you have saved your *xorg.conf* do not simply exit, but **reboot**: ALT+BK_SPACE will not work. HTH

---

### Post by norwoods on 2009-03-30
did you click the Detect Displays button in X Server Display Configuration with your new monitor plugged in and turned on?

---

### Post by skotos on 2009-04-30
> **norwoods said:**
> did you click the Detect Displays button in X Server Display Configuration with your new monitor plugged in and turned on?
The previous driver version - 177 - worked fine in Hardy, version 180 does not display the screen numbers under Jaunty.

FYI - I have always been plugging in any external monitor when the notebook is switched off.

In the past, many adapters were able to successfully detect any external device at startup only, thus I have kept this habit along the years. I think it is a good practice in order to avoid/limit any motherboard shock, too: static electricity is all around and deadly aggressive...

---

### Post by don_eros on 2009-04-30
> **skotos said:**
> 
FYI - I have always been plugging in any external monitor when the notebook is switched off.


So do I, the problem is not that, I tried everything I could think of and finally decided to submit a bug to launchpad:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/353067](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/353067)

Thanks anyway.

---

