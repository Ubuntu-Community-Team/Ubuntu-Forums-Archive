---
title: "Intel-HDA Headphone problem"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by hersel on 2007-02-04
Hello

I'm not able to switch on the headphone output on my notebook.

Configuration:
Notebook: HP Pavilion dv9097ea
Ubunto 6.10
Jack layout on front: 1 Mic-in, 1 Audio-out chinch, 1 Audio-SPDIF-out
chinch

Soundcard and Codec:
        ralf@hersel-r:~$ cat /proc/asound/cards
        0 [Intel ]: HDA-Intel - HDA Intel
        HDA Intel at 0xde300000 irq 66
        1 [Headset ]: USB-Audio - Logitech USB Headset
        Logitech Logitech USB Headset at usb-0000:00:1d.0-2, full speed

        ralf@hersel-r:~$ head -n 1 /proc/asound/card0/codec*
        Codec: Generic 14f1 ID 50

ALSA-Mixer shows only 3 controls: Master, PCM, In-Gain.
I tried all possible combination of control settings without success.

I tried these settings in /etc/modprobe.d/alsa-base:
        3stack-digout
        z71v
        auto
        3stack-dig
Have not tried any 'position-fix' settings.

Thanks a lot for your help.
Regards
Ralf

---

### Post by mikewhatever on 2007-02-04
I do not think there is a special switch for that. What happens when you plug the headphones in? Is there sound from the speakers, or no sound at all?

You may need to reinstall the driver. Check [THIS GUIDE]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29")

---

### Post by hersel on 2007-02-05
When I plug in the headphones nothing happens: no sound on the headphones, notebook speakers continue to play.
In the meantime I've got in contact with a developer from the ALSA team. He said:

"Based on this line, you are running an older version of alsa-driver.
Partial support has been added in alsa-driver-1.0.14rc2, and I am
currently working on full functionality at this time.  I have added you
to my tester's mailing list, so you can be kept up with the development.
Email me directly if you have issues.

Start by downloading alsa-driver-1.0.14rc2.tar.bz2.  I'll send you a
separate email with instructions and the latest test patch."

I will try to install the latest driver.
Thanks
Ralf

---

### Post by sspingal on 2008-04-08
Guys try this link called Envy.
It worked for me. I am using Acer Aspire 4710z.

"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you


[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

All the best.

---

