---
title: "Voice recorders under Ubuntu"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by Dafydd on 2007-11-13
Hi,

I want to buy a "voice recorder" (olympus, philips etc). I'm a journalist and need to be able to transfer the recorder speech files to my Ubuntu computer as it is easier to transcribe.

Has anyone any idea of what make is better? I've tried using colleagues voice recorders (Olympus and Philips) and could either not access the voice recorder or could not use the file. Is anyone using a voice recorder and just plugging it into an Ubuntu machine to transfer files? What voice recorder is it?

Thanks for info

Dafydd

---

### Post by Dafydd on 2007-11-17
No replies! but saw some where on the web something about the Olympus WS-100. But I could only find the WS110 at Mediamarkt for EUR 98 . It only has 256MB but records in WMA format and is recognised by Ubuntu like a USB key. So everything is fine.

Apparently don't buy Olympus VN series (that is if you want to listen to the recorded files on your Ubuntu machine - or email them if necessary.)

Dafydd

---

### Post by Dafydd on 2007-12-11
> **Dafydd said:**
> No replies! but saw some where on the web something about the Olympus WS-100. But I could only find the WS110 at Mediamarkt for EUR 98 . It only has 256MB but records in WMA format and is recognised by Ubuntu like a USB key. So everything is fine.

After a while I realised I wanted to play my own files (music, radio etc) on the voice recorder. Unfortunately, they have to be converted (using ffmpeg or CONVERIT) to WMA first.

I think the WS 300 (at 150EUR) natively plays mp3.
Dafydd

---

### Post by detroit/zero on 2007-12-13
Well, I wish I would have checked the forums before I went to the store..

I just bought an Olympus VN-3100PC voice recorder. It comes with a Windows XP/Vista and Apple software CD, but as usual, Linux support is absent.

Ordinarily, when something is plugged into the USB it autodetects fairly rapidly, but that's not the case here. This thing doesn't detect at all. The recorder registers that it is connected to a PC, but Ubuntu doesn't detect the recorder. It doesn't even show up in an lspci check.

Anybody have any ideas? I don't want to have to use Vista when I need to download the files from my recorder.

I'm using Feisty on a Toshiba Satellite A135, by the way. I have another machine with Gutsy installed but haven't tried it on that one yet.

I'm not sure what if any other info to provide about my machine.

Thanks for any help.

---

### Post by Dafydd on 2008-04-26
> **detroit/zero said:**
> I just bought an Olympus VN-3100PC voice recorder. It comes with a Windows XP/Vista and Apple software CD, but as usual, Linux support is absent. Ordinarily, when something is plugged into the USB it autodetects fairly rapidly, but that's not the case here. This thing doesn't detect at all. The recorder registers that it is connected to a PC, but Ubuntu doesn't detect the recorder. It doesn't even show up in an lspci check.

i was lucky to have borrowed three different olympus and philips voice recorders before buying mine. VN sucks if you are on linux and WS just works natively. Still, I have to use ffmpeg to convert to WMA just to play stuff on my Olympus WS110. That said listening and editing the WMA recordings i make is fine (just convert them to au or wav).

detroit/zero, perhaps someone has found some magic way to make the VN series work, but if not try a WS Olympus.

---

### Post by detroit/zero on 2008-04-26
> **Dafydd said:**
> detroit/zero, perhaps someone has found some magic way to make the VN series work, but if not try a WS Olympus.

I'm sort of stuck with the one I have. I found a half-assed workaround for the problem, though:

Occasionally, I find a need for Windows specific software and there's no Linux equivalent or anything. I have XP in a virtual machine that I keep on ice for just such occasions, and the Olympus software is such an occasion.

---

