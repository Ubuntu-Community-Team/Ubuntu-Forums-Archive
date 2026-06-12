---
title: "VOIP USB Phones: Ubuntu/Linux no good for this?"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by joeybutterface on 2007-07-29
So I've happily migrated from Windows to Ubuntu Linux on my laptop (having already replaced Windows XP with CentOS 5 on my Desktop). I have almost everything running the way I want. The essential Windows productivity applications like Photoshop and Dreamweaver running under Crossover Linux. My external hard drives working upon USB connection. Audio, wireless, CD and DVD burning all flawlessly operational.

However, I've suddenly become interested in Skype/VOIP and it seems I've stumbled across something Linux has pretty terrible support for. In particular, USB Phones and Handsets. I've searched numerous forums for supported hardware that isn't next to impossible to get working on Ubuntu/Linux and it appears there is close to nothing recommended. 

Most manufacturers of these devices apparently don't care about Linux, and refuse to provide any kind of drivers for their devices. 3com, Philips, USRobotics etc.

There are numerous unanswered threads here from people begging for help getting their VOIP phones working under Ubuntu having had no success themselves. I've scrolled through 4-5 months of postings in the Linux forum on Skype and numerous requests from people for recommendations for supported Linux USB phones to buy also either go unanswered. Occasionally some kind hearted soul provides a couple of links to other resources that suggest IT MIGHT be possible to get something going on a KDE Linux machine using one particular type of driver. Or better still, set up an entire VOIP server to replace your old PSTN line with this new wondrous technology that will save you thousands of dollars a year.

I've been dabbling with Linux for several years now. Usually I find with enough research and patience, a solution can usually be found for a problem. But having Googled for days and spent more time than I care to think about searching forums for every conceivable set of keywords, I've been left totally frustrated no better clued up about a solution. This is doubly frustrating having successfully got the latest Skype software to run after overcoming several stumbling blocks.

The conclusion I'm about to draw is if I want a good Skype/VOIP experience using a USB Phone I had better reach for the Windows XP reinstall disc.

---

### Post by vcallaway on 2007-07-29
Frankly this seems like a non-issue.

I for one am not really interested in having a phone tethered to my computer.  It has enough things to do as it is.

I've been thinking about the Linksys CIT400 unit.  Just plug the box in my hub and go.

---

### Post by ugm6hr on 2007-07-30
I use a simple (and very cheap) headset for my laptop.  Just plug into the headphone / microphone sockets, and make use of the built-in sound card.  Skype / Ekiga work fine now that I've sorted that.  It's totally multi-OS, and allows use as a microphone for other purposes.

---

### Post by catan85 on 2007-09-11
I've a problem like your with my Philips VOIP321 phone... I think it's impossible
to make it working under ubuntu... isn't true?

Thanks Cattan

---

### Post by YannickDefais on 2007-09-12
Hi,

I've a solution, but it's not user friendly yet:
[http://wiki.ekiga.org/index.php/Controling_Ekiga_using_an_USB_phone](http://wiki.ekiga.org/index.php/Controling_Ekiga_using_an_USB_phone)

Regards,
Yannick

---

### Post by markusr on 2007-09-24
I just bought Logitech Quicall USB Phone...

It was detected an installed automatically.

mr@mr:~/Desktop$ cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SBLive 5.1 [SB0060]
                      SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) at 0xa000, irq 20
 1 [SpeakerphoneDis]: USB-Audio - Speakerphone(Disabled)
                      Speakerphone(Disabled) at usb-0000:00:02.0-3, full speed
mr@mr:~/Desktop$ ls -l /dev/dsp*
crw-rw---- 1 root audio 14,  3 2007-09-24 12:30 /dev/dsp
crw-rw---- 1 root audio 14, 19 2007-09-24 12:30 /dev/dsp1
mr@mr:~/Desktop$ ls -l /dev/audio*
crw-rw---- 1 root audio 14,  4 2007-09-24 12:30 /dev/audio
crw-rw---- 1 root audio 14, 20 2007-09-24 12:30 /dev/audio1
mr@mr:~/Desktop$ 


sound out works fine
but sound in doesn't work
LEDs keep flashing due to the missing driver...

i think it is not possible to "enable" it with linux

tried for hours to get the mic to work - i'll get my money back :(

---

### Post by pregister on 2008-01-29
HI I am  total newbie in Ubuntu[ignorance is apparently bliss]plugged in my us  robotics phone in,did not work in skype.Went in skype controls selected usb device for audio and video.Phone looks like it is not responding,but when I press in numbers it goes to screen and dials out just fine.Not a high tech soulution but I hope it helps someone.
                                                  Thanks to Ubuntu community ,
                                                  I LOVE THIS OS
                                    [Goodbye mickey soft]:lolflag:

---

### Post by pregister on 2008-01-29
Me again ,forgot to mention phone is usr 9601. 
                                                                 Pregister

---

### Post by oldsoundguy on 2008-01-29
I use a regular phone plugged into a D-Link VoIP router/hub and that is plugged into my network.  Saves all kinds of grief. It even has the proviso for a SECOND line when my ISP decides to make that available.
But it would seem that if SKYPE is a workable thing in Ubunty (not tried it) .. the USB stuff SHOULD work.

---

