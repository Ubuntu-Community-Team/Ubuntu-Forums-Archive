---
title: "Mplayer subtitles"
date: 2005-12-04
forum: General Help
---

### Post by Jeff Eklund on 2005-12-04
Hi! I recently installed Ubuntu on a friends laptop and he's now complaining about the subtitles in mplayer and xine. They are too small. He tried using Mplayer, Totem, Xine, Kaffeine, gXine and VLC, but some of them didn't even play his .srt-subtitle file. VLC played it partially, showing the first line, skipping the next three lines, then showing another line and so on. But the common error among all the players that DID show the subtitles was that they were extremely small, and they didn't become larger when he played the file in fullscreen. He tried changing the fontsize from whitin the programs that allowed such changing and he tried modifying ~/.gnome2/totem_config but with no luck. The last thing he tried was to edit the ~/.mplayer/config-file but he didn't have any, abd he can't seem to find any copy of the original file on the internets, so he can't copy it and modify it.
Can someone help me help him? Does someone know why the subtitles turn small or why they don't show up at all? Could someone post his/her mplayer-config or xine-config files so that we might see what's wrong with my buddys?
Thanks alot in advance!

---

### Post by ow50 on 2005-12-04
MPlayer has by far the best subtitle rendering in terms of antialiasing and configurability. Here's my ~/.mplayer/config part dealing with subtitles
```
#==========
# Subtitles
#==========

# VobSubs
#========

# Align subs. (-1: as they want to align themselves)
spualign=-1

# Anti-alias subs. (4: best and slowest)
spuaa=4

# Set language.
slang=fi,fin,en,eng

# Text-based subtitles
#=====================

# Find subtitle files. (1: load all subs containing movie name)
sub-fuzziness=1

# Set font.
font=/home/osmo/.fonts/microsoft-vista/calibri.ttf

# Set font encoding.
subfont-encoding=unicode

# Set subtitle file encoding.
unicode=yes
utf8=yes

# Resample the font alphamap. (10: bold black outline)
ffactor=10

# Set subtitle position. (100: as low as possible)
subpos=100

# Set subtitle alignment at its position. (2: bottom)
subalign=2

# Set font size. (2: proportional to movie width)
subfont-autoscale=2

# Set font blur radius. (default: 2)
subfont-blur=1.1

# Set font outline thickness. (default: 2)
subfont-outline=1.2

# Set autoscale coefficient. (default: 5)
subfont-text-scale=4.2

# OSD
#====

# Set autoscale coefficient. (default: 6)
subfont-osd-scale=4.2
```
At minimum you need to change the font path and then play with the subfont-text-scale and subfont-osd-scale values.

---

### Post by Jeff Eklund on 2005-12-04
Hi! 
Thanks for your config! I tried it and tries just changing the fontpath to one of my own; font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf
But when I start Mplayer it says: ```
New_Face failed. 
Maybe the font path is wrong. 
Please supply the text font file (~/.mplayer/subfont.ttf)
```
What does that mean?

---

### Post by ow50 on 2005-12-04
[QUOTE=Jeff Eklund]I tried it and tries just changing the fontpath to one of my own; font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf
But when I start Mplayer it says: ```
New_Face failed. 
Maybe the font path is wrong. 
Please supply the text font file (~/.mplayer/subfont.ttf)
```
What does that mean?[/QUOTE]
That exact fontpath works for me. MPlayer tells me
```
/usr/share/fonts/truetype/msttcorefonts/arial.ttf doesn't look like a font description, ignoring.
Cannot load font: /usr/share/fonts/truetype/msttcorefonts/arial.ttf
```
but works regardless.

You could try symlinking that Arial font to where MPlayer apparently wants it
```
ln -s /usr/share/fonts/truetype/msttcorefonts/Arial.ttf ~/.mplayer/subfont.ttf
```
and setting the font to ~/.mplayer/subfont.ttf or commenting out the font setting.

---

### Post by Jeff Eklund on 2005-12-05
Thnaks that worked fine! But I now experience another error: all special characters lika å(å), ä(ä), ö(ö) (I'm swedish), show up as underscores!
Another error: my friend reports that the same error with the special characters and that his Mplayer screen refuses to stretch his image when going into fullscreen. It stretches the picture just a bit, but leaves a couple of centimeters to the edges in every direction, both up/down and to the right/left. This is just some other setting that hes gotten wrong. how do I help him fix it?
Thanks again for your help! :-)

PS. Nice seeing someone else from Scandinavia here.

---

### Post by ow50 on 2005-12-05
> **Jeff Eklund]But I now experience another error: all special characters lika å(å), ä(ä), ö(ö) (I'm swedish), show up as underscores![/QUOTE]
In the config file I posted, you'd need to change these lines
```
# Set font encoding.
subfont-encoding=unicode

# Set subtitle file encoding.
unicode=yes
utf8=yes
```
to something else. At least the two lower lines to "no". I'm not sure if you need to change the subfont-encoding.

The problem is that most subs that you can download from various websites are encoded with some windows encoding, perhaps windows-1252 (a.k.a. cp1252) or something compatible, while Ubuntu's default character encoding is UTF-8. I have a habit of converting the subs to UTF-8, since I often might do spell-checking and error-corrections.

So the other option would be converting the subs to UTF-8 with the following terminal command
```
iconv -f cp1252 -t utf8 infile.srt -o outfile.srt
```
For easy use you could make a Nautilus script, for example:
```
#!/bin/bash
for arg said:**
> Another error: [...] Mplayer screen refuses to stretch his image when going into fullscreen. It stretches the picture just a bit, but leaves a couple of centimeters to the edges in every direction, both up/down and to the right/left. This is just some other setting that hes gotten wrong. how do I help him fix it?
My guess is that your friend is using the wrong video driver. If he's using GMPlayer, the video driver can be changed in the preferences dialog. If he's using MPlayer, he can get a list of valid video drivers with the command
```
mplayer -vo help
```
It will list plenty. The most common ones should be "x11" and "xv". Then try them, for example
```
mplayer -vo xv <filename>
```
And once he finds one that works he can put it in the config file, for example with the line "vo=xv".

---

