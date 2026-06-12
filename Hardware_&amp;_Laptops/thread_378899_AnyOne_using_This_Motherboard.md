---
title: "AnyOne using This Motherboard?"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by Demz on 2007-03-07
anyone here using Fiesty fawn or anyone using ubuntu with the  Motherboard **GA-M59SLI-S5** Being Gigabyte that is, i did search but no results found

---

### Post by nawz on 2007-03-11
Ii just installed 6.10 on the sa-m59sli-s5. I had to use the noapic option to get the installer to go through.
System is running great with beryl and looks beautiful.
 
My only issue is the on board sound starts to play then begins a 1 second loop. (like a stuck record!). I have to kill the app to make it stop the noise.

It uses the alc883 / mcp55 HD audio chipset.
And i have installed the right drivers for OSS and alsa(?) intel80x
All the necessary codecs are installed.
Video card is a geforce 7900gs.
AMD x2 64 4900+

After a entire day dedicated to google and these forums i have only succeeded in getting Audio to play and Video... But not at the same time. The audio again starts to play then gets stuck in a loop. Ive tried VLC, Mplayer, XMMS, you name it, Each of these apps will play mp3's etc, They will play Video with no sound output chosen. I try both and it just gets stupid.
Please any help would be greatly appreciated as ive exhausted all my resources for finding a solution to this.

---

### Post by Demz on 2007-03-11
> **nawz said:**
> Ii just installed 6.10 on the sa-m59sli-s5. I had to use the noapic option to get the installer to go through.
System is running great with beryl and looks beautiful.
 
My only issue is the on board sound starts to play then begins a 1 second loop. (like a stuck record!). I have to kill the app to make it stop the noise.

It uses the alc883 / mcp55 HD audio chipset.
And i have installed the right drivers for OSS and alsa(?) intel80x
All the necessary codecs are installed.
Video card is a geforce 7900gs.
AMD x2 64 4900+

After a entire day dedicated to google and these forums i have only succeeded in getting Audio to play and Video... But not at the same time. The audio again starts to play then gets stuck in a loop. Ive tried VLC, Mplayer, XMMS, you name it, Each of these apps will play mp3's etc, They will play Video with no sound output chosen. I try both and it just gets stupid.
Please any help would be greatly appreciated as ive exhausted all my resources for finding a solution to this.
thank you for that, 
 i currently have 2 systems atm but i wil be giving my Old one to my mother, so this information comes in handy to install ubuntu on this motherboard,  only thing i got a ATI x1600 512MB card but all should be fine, an BIOS is up to date to

---

### Post by nawz on 2007-03-12
I am a new linux user with very basic knowledge of the OS. So please forgive my ignorance.

During install i get a apic timer doesn't work error so  I had to install with the noapic option.

I am wondering if this may be the root cause of my sound / video issue. Could anyone shed some light on  apic and what it exactly does? From what i have read it is related to system timing....which leads me to think this is the cause of my multimedia playback issue.

---

