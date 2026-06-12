---
title: "S-Video output very blurry from my laptop"
date: 2009-09-10
forum: Hardware
---

### Post by Sam The Bam 4 on 2009-09-10
Hi Fellas.

  OK I have a laptop with an Integrated Intel GMA 950 GPU that offers both S-Video and VGA out connections for outputing to an external screen.

  Now because my lappy's screen is broken, I have to use a seperate one, but as I don't have a VGA cable handy just now, I have to use a 4-pin S-Video connection.

  I'm feeding the video into a Sharp LC-20SH1E 20' LCD TV.

 The problem is, both In windows 7 and on Ubuntu 9.04, the picture is very low-resolution, y'know, blurry, and especially text is barely ledgible,the picture has a very grainy-hazy look to the edges of things like text.

  Even turning down resolution doesn't help much, and the refresh rate is stuck at 30Hz, won't let us go any higher , even though the TV aparently can support 1024x768 and 60Hz.

  Can anyone give us a hand on what I could try to improve the picture?
  Cheers fellas
Sam The Bam

---

### Post by theirishfozz on 2009-09-10
Hi Sam

I have the same problem, if it can be called a problem. 

From the S-Video wiki:
"This differs from composite video, which carries picture information as a single lower-quality signal, and component video, which carries picture information as three separate higher-quality signals. S-Video carries standard definition video (typically at 480i or 576i resolution), but does not carry audio on the same cable."

Your best bet is to set your desktop resolution to 720x480 to match NTSC resolution if you want to keep using s-video.

I have an ubuntu server set up piping s-video out to an old tv. My motherboard has hdmi but I can't use it till I get a new tv :(. It looks VERY blurry and is almost impossible to use for normal operations BUT I use it as a media centre and it works perfectly for that. Small text is hard to read but that's not an issue in MythTV. 

I'm not really sure what to suggest you do. Everywhere I've looked for that TV say it can support 640x480 and does not have vga or dvi. I think your best bet is to get an actual monitor which can be done for ~$100.

I hope this helps

Fozz

---

