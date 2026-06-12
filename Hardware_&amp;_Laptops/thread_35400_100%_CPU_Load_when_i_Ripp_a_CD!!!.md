---
title: "100% CPU Load when i Ripp a CD!!!"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by FreeEagle on 2005-05-18
Hi all,

I have a question !!!! Why when i ripp a CD the CPU is to 100% loaded?? is this normal?? Or i missed somthing here ?? 

See the Attached Photo!!!!


Best Regards,
 FreeEagle

---

### Post by jeremy on 2005-05-19
Do you have dma on for your cd drive?

---

### Post by az on 2005-05-19
Are you encoding while you rip?

---

### Post by JonahRowley on 2005-05-19
You're encoding the audio.  Encoding MP3 or Ogg is computationally expensive, this is perfectly normal.

---

### Post by FreeEagle on 2005-05-19
[QUOTE=azz]Are you encoding while you rip?[/QUOTE]

yes ... I did encoding while i was Ripping...



FreeEagle

---

### Post by FreeEagle on 2005-05-19
[QUOTE=jeremy]Do you have dma on for your cd drive?[/QUOTE]

and what is this then ? I am a Newbie , so can you tell what is this please!!!


FreeEagle

---

### Post by Hamman on 2005-05-19
Encoding is VERY CPU-intesive, so nothing is wrong.

---

### Post by jeremy on 2005-05-19
[QUOTE=FreeEagle]and what is this then ? I am a Newbie , so can you tell what is this please!!!


FreeEagle[/QUOTE]
 try
sudo hdparm /dev/hdc (where hdc is your cd drive).

---

### Post by pointym5 on 2005-05-19
On my system at least, *hdparm* doesn't succeed in turning DMA on for my CD ROM. It fails with an ioctl error.

---

### Post by logan2004 on 2005-05-19
[QUOTE=Hamman]Encoding is VERY CPU-intesive, so nothing is wrong.[/QUOTE]

[QUOTE=JonahRowley]You're encoding the audio.  Encoding MP3 or Ogg is computationally expensive, this is perfectly normal.[/QUOTE]

[QUOTE=Hamman]Encoding is VERY CPU-intesive, so nothing is wrong.[/QUOTE]

gg's

---

### Post by jeremy on 2005-05-20
[QUOTE=pointym5]On my system at least, *hdparm* doesn't succeed in turning DMA on for my CD ROM. It fails with an ioctl error.[/QUOTE]
 look here;
[http://ubuntuforums.org/showpost.php?p=93238&postcount=5](http://ubuntuforums.org/showpost.php?p=93238&postcount=5)

---

### Post by FreeEagle on 2005-05-20
Thanks very much for the Replay.....



Best Regards,
 FreeEagle

---

