---
title: "USB flash device mounted as a music player"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by spinstartshere on 2007-05-14
When I connect a USB flash drive to my computer, it is mounted as a music player.  This has only started happening recently and I do not know what might have caused this change.  How can I stop it being mounted as a media player and have it mount as a removable storage device, as it did before?

---

### Post by Unicast on 2007-05-18
Does anyone else see this?

Must admit I get this as well - my flash drives show up as digital media players with an ipod / headphones icon on the desktop.

Is there a quick and easy fix?

---

### Post by currentshades on 2007-05-24
I am getting the same problem.  I have a Corsair Flash Voyager, 2GB, with no security features (etc.) enabled.  It's a minimal problem, but it is annoying to have my music player start up when I insert my USB flash drive.

---

### Post by djaya2 on 2007-05-28
Bump.  Anyone?

Same problem here, with a Corsair Flash Voyager 4 GB.  I think maybe this is preventing my VM from detecting my flash drive, which is a big problem for me because I have an app I need to use in Windows, and a flash drive is the easiest way to share files, as far as I can tell.

---

### Post by GrumpyBob on 2007-05-29
The same here (since a week or two ago), Feisty on a Sony Vaio TX5XN.

Robert

---

### Post by spinstartshere on 2007-05-29
I do not know if this is a contributing factor, but I do remember installing Amarok shortly before experiencing this problem.

---

### Post by GrumpyBob on 2007-05-30
I installed gtkpod shortly beforehand!

Robert

---

### Post by djaya2 on 2007-05-31
It happened to me after I ran:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Anyone?

---

### Post by Jose Catre-Vandis on 2007-06-08
I get it too, posted about it but got no replies. Fiesty calls my usb drive an ipod, and opens rythymbox

---

### Post by CrispyFried on 2007-06-08
are any MP3s on the drive? that might trigger an audio player app to flag it as a music device.

check around in your audio players and see if any of them auto check new devices.

---

### Post by spinstartshere on 2007-06-08
There's none on mine.

---

### Post by Jose Catre-Vandis on 2007-06-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/90286](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/90286) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey Guys, found a possible answer for this, works for me.

Picked up the solution from here:

[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/90286](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/90286)

To handle this manually, insert your offending flash drive, and once loaded run
```
lsusb
```
my output is as follows:
```
tim@fiesty:~$ lsusb
Bus 005 Device 006: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Remove your flash drive

The "Feiya Technology Corp. Memory Bar" is what we are looking for, yours might be a different model but the fix should be the same. This device carries the same product ID as other products that are music players. We need to remove the entry from:

```
/usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi
```

First do a back up in case anything goes wrong:
```
sudo cp /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi.bak
```

Then open up /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi as root:
```
sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi
```

Scroll down through the file until you find the entry for your disk:
```
<append key="portable_audio_player.input_formats" type="strlist">audio/x-ms-wma</append>
          </match>
	</match>

       [B] <!-- Feiya Technology Corp Memory Bar -->
        <match key="@storage.originating_device:usb.vendor_id" int="0x090c">
          <match key="@storage.originating_device:usb.product_id" int="0x1000">
            <merge key="portable_audio_player.type" type="string">generic</merge>
            <merge key="portable_audio_player.access_method" type="string">storage</merge>
            <append key="portable_audio_player.input_formats" type="strlist">audio/mpeg</append>
          </match>
        </match>[/B]

	<!-- Peak Digital Audio Player -->
        <match key="@storage.originating_device:usb.vendor_id" int="0xd7d">
```

Delete the bolded section, and save and close the file.

Reinsert your flash drive and it should now appear as a flash drive/disk and not invoke the music app!

This action may get broken again by hal backports or updates, until the devs sort it out.

If it doesn't work, restore your original .fdi file

Hope this helps (you do all this at your own risk, I can't take responsibility if this does damage to your system!)

---

### Post by Unicast on 2007-06-27
Nice one, worked like a charm. ;)

And thanks for the PM alerting me to your post! :D

---

### Post by djaya2 on 2007-08-27
Thanks, worked for me too.

---

### Post by Glsg on 2007-09-11
I've tried this workaround, and it works concerning the wrong recognization, but I'm not able to mount the device. :(
Anyone could help?

(thanks in advance, and sorry 4 my english, I'm italian)

---

### Post by zeroword on 2008-07-12
I tried but I could not find a Feiya Memory Bar entry anywhere.

---

