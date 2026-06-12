---
title: "1) dvd file copy issues 2) multimedia playback"
date: 2008-08-09
forum: General Help
---

### Post by jadhav333 on 2008-08-09
**os** : ubuntu - 8.04
**m/c** : quad core 2.4 ghz, 4 gb ram.
**graphics card** : nvidia 8600 gts (restricted nvidia drivers installed)
**interface : **gnome

1) unable to copy vob files (larger than 500mb) from dvd.. to local hard disk. 

2) quality of video playback is not so good and sometimes jerky.. in totem player after installing gstreamer codecs.. and also on gxine player

3) also.. can i run KDE based applications while the desktop is gnome based. will it cause issues??

Pls advise.

---

### Post by jadhav333 on 2008-08-10
pls respond..

---

### Post by Vivaldi Gloria on 2008-08-10
> 1) unable to copy vob files (larger than 500mb) from dvd.. to local hard disk. 

What do you mean by unable? Is this with a particular dvd or with all dvds? Try copying in the terminal and see if you get any errors.

> 2) quality of video playback is not so good and sometimes jerky.. in totem player after installing gstreamer codecs.. and also on gxine player

Sorry. Don't know this one. Try vlc or gnome-mplayer for a change.

> 3) also.. can i run KDE based applications while the desktop is gnome based. will it cause issues??


You can use them without a problem.

---

### Post by jadhav333 on 2008-08-11
> **Vivaldi Gloria said:**
> What do you mean by unable? Is this with a particular dvd or with all dvds? Try copying in the terminal and see if you get any errors.



PFA, the screenshot of the error message and the file list of the folder to which it is copied..

This happens with  all DVDs I have tried.. This disk is a 7GB Disk.

it copies most of the smaller files.. moment we reach the vob files.. bingo.. up comes this error message..

---

### Post by cariboo on 2008-08-11
Can you create an iso file of your dvd? To do it, in a terminal type:

```
sudo dd if=/dev/dvd of=somedvd.iso
```

Also do you have enough room on your partition to copy the files?

Jim

---

### Post by jadhav333 on 2008-08-11
i tried the iso option.. it got the same error..

also here is a transcript of the copy operation through the terminal.. i have highlighted the error messages in red.. 

also.. there is ample space on the partition.. :)

> 
`/cdrom/' -> `./cdrom'
`/cdrom/AUDIO_TS' -> `./cdrom/AUDIO_TS'
`/cdrom/Autorun.inf' -> `./cdrom/Autorun.inf'
`/cdrom/ShelExec.exe' -> `./cdrom/ShelExec.exe'
`/cdrom/VIDEO_TS' -> `./cdrom/VIDEO_TS'
`/cdrom/VIDEO_TS/VIDEO_TS.BUP' -> `./cdrom/VIDEO_TS/VIDEO_TS.BUP'
`/cdrom/VIDEO_TS/VIDEO_TS.IFO' -> `./cdrom/VIDEO_TS/VIDEO_TS.IFO'
`/cdrom/VIDEO_TS/VIDEO_TS.VOB' -> `./cdrom/VIDEO_TS/VIDEO_TS.VOB'
`/cdrom/VIDEO_TS/VTS_01_0.BUP' -> `./cdrom/VIDEO_TS/VTS_01_0.BUP'
`/cdrom/VIDEO_TS/VTS_01_0.IFO' -> `./cdrom/VIDEO_TS/VTS_01_0.IFO'
`/cdrom/VIDEO_TS/VTS_01_0.VOB' -> `./cdrom/VIDEO_TS/VTS_01_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_01_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_01_1.VOB' -> `./cdrom/VIDEO_TS/VTS_01_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_01_1.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_02_0.BUP' -> `./cdrom/VIDEO_TS/VTS_02_0.BUP'
`/cdrom/VIDEO_TS/VTS_02_0.IFO' -> `./cdrom/VIDEO_TS/VTS_02_0.IFO'
`/cdrom/VIDEO_TS/VTS_02_0.VOB' -> `./cdrom/VIDEO_TS/VTS_02_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_02_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_02_1.VOB' -> `./cdrom/VIDEO_TS/VTS_02_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_02_1.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_03_0.BUP' -> `./cdrom/VIDEO_TS/VTS_03_0.BUP'
`/cdrom/VIDEO_TS/VTS_03_0.IFO' -> `./cdrom/VIDEO_TS/VTS_03_0.IFO'
`/cdrom/VIDEO_TS/VTS_03_0.VOB' -> `./cdrom/VIDEO_TS/VTS_03_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_03_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_03_1.VOB' -> `./cdrom/VIDEO_TS/VTS_03_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_03_1.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_04_0.BUP' -> `./cdrom/VIDEO_TS/VTS_04_0.BUP'
`/cdrom/VIDEO_TS/VTS_04_0.IFO' -> `./cdrom/VIDEO_TS/VTS_04_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_04_0.VOB' -> `./cdrom/VIDEO_TS/VTS_04_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_04_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_04_1.VOB' -> `./cdrom/VIDEO_TS/VTS_04_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_04_1.VOB': Input/output error[/COLOR]
`/cdrom/VIDEO_TS/VTS_05_0.BUP' -> `./cdrom/VIDEO_TS/VTS_05_0.BUP'
`/cdrom/VIDEO_TS/VTS_05_0.IFO' -> `./cdrom/VIDEO_TS/VTS_05_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_05_0.VOB' -> `./cdrom/VIDEO_TS/VTS_05_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_05_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_05_1.VOB' -> `./cdrom/VIDEO_TS/VTS_05_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_05_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_06_0.BUP' -> `./cdrom/VIDEO_TS/VTS_06_0.BUP'
`/cdrom/VIDEO_TS/VTS_06_0.IFO' -> `./cdrom/VIDEO_TS/VTS_06_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_06_0.VOB' -> `./cdrom/VIDEO_TS/VTS_06_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_06_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_06_1.VOB' -> `./cdrom/VIDEO_TS/VTS_06_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_06_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_07_0.BUP' -> `./cdrom/VIDEO_TS/VTS_07_0.BUP'
`/cdrom/VIDEO_TS/VTS_07_0.IFO' -> `./cdrom/VIDEO_TS/VTS_07_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_07_0.VOB' -> `./cdrom/VIDEO_TS/VTS_07_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_07_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_07_1.VOB' -> `./cdrom/VIDEO_TS/VTS_07_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_07_1.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_07_2.VOB' -> `./cdrom/VIDEO_TS/VTS_07_2.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_07_2.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_07_3.VOB' -> `./cdrom/VIDEO_TS/VTS_07_3.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_07_3.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_07_4.VOB' -> `./cdrom/VIDEO_TS/VTS_07_4.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_07_4.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_07_5.VOB' -> `./cdrom/VIDEO_TS/VTS_07_5.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_07_5.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_08_0.BUP' -> `./cdrom/VIDEO_TS/VTS_08_0.BUP'
`/cdrom/VIDEO_TS/VTS_08_0.IFO' -> `./cdrom/VIDEO_TS/VTS_08_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_08_0.VOB' -> `./cdrom/VIDEO_TS/VTS_08_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_08_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_08_1.VOB' -> `./cdrom/VIDEO_TS/VTS_08_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_08_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_09_0.BUP' -> `./cdrom/VIDEO_TS/VTS_09_0.BUP'
`/cdrom/VIDEO_TS/VTS_09_0.IFO' -> `./cdrom/VIDEO_TS/VTS_09_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_09_0.VOB' -> `./cdrom/VIDEO_TS/VTS_09_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_09_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_09_1.VOB' -> `./cdrom/VIDEO_TS/VTS_09_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_09_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_10_0.BUP' -> `./cdrom/VIDEO_TS/VTS_10_0.BUP'
`/cdrom/VIDEO_TS/VTS_10_0.IFO' -> `./cdrom/VIDEO_TS/VTS_10_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_10_0.VOB' -> `./cdrom/VIDEO_TS/VTS_10_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_10_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_10_1.VOB' -> `./cdrom/VIDEO_TS/VTS_10_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_10_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_11_0.BUP' -> `./cdrom/VIDEO_TS/VTS_11_0.BUP'
`/cdrom/VIDEO_TS/VTS_11_0.IFO' -> `./cdrom/VIDEO_TS/VTS_11_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_11_0.VOB' -> `./cdrom/VIDEO_TS/VTS_11_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_11_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_11_1.VOB' -> `./cdrom/VIDEO_TS/VTS_11_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_11_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_12_0.BUP' -> `./cdrom/VIDEO_TS/VTS_12_0.BUP'
`/cdrom/VIDEO_TS/VTS_12_0.IFO' -> `./cdrom/VIDEO_TS/VTS_12_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_12_0.VOB' -> `./cdrom/VIDEO_TS/VTS_12_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_12_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_12_1.VOB' -> `./cdrom/VIDEO_TS/VTS_12_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_12_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_13_0.BUP' -> `./cdrom/VIDEO_TS/VTS_13_0.BUP'
`/cdrom/VIDEO_TS/VTS_13_0.IFO' -> `./cdrom/VIDEO_TS/VTS_13_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_13_0.VOB' -> `./cdrom/VIDEO_TS/VTS_13_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_13_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_13_1.VOB' -> `./cdrom/VIDEO_TS/VTS_13_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_13_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_14_0.BUP' -> `./cdrom/VIDEO_TS/VTS_14_0.BUP'
`/cdrom/VIDEO_TS/VTS_14_0.IFO' -> `./cdrom/VIDEO_TS/VTS_14_0.IFO'
`/cdrom/VIDEO_TS/VTS_14_0.VOB' -> `./cdrom/VIDEO_TS/VTS_14_0.VOB'
[COLOR="Red"]cp: reading `/cdrom/VIDEO_TS/VTS_14_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_14_1.VOB' -> `./cdrom/VIDEO_TS/VTS_14_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_14_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_15_0.BUP' -> `./cdrom/VIDEO_TS/VTS_15_0.BUP'
`/cdrom/VIDEO_TS/VTS_15_0.IFO' -> `./cdrom/VIDEO_TS/VTS_15_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_15_0.VOB' -> `./cdrom/VIDEO_TS/VTS_15_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_15_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_15_1.VOB' -> `./cdrom/VIDEO_TS/VTS_15_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_15_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_16_0.BUP' -> `./cdrom/VIDEO_TS/VTS_16_0.BUP'
`/cdrom/VIDEO_TS/VTS_16_0.IFO' -> `./cdrom/VIDEO_TS/VTS_16_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_16_0.VOB' -> `./cdrom/VIDEO_TS/VTS_16_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_16_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_16_1.VOB' -> `./cdrom/VIDEO_TS/VTS_16_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_16_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_17_0.BUP' -> `./cdrom/VIDEO_TS/VTS_17_0.BUP'
`/cdrom/VIDEO_TS/VTS_17_0.IFO' -> `./cdrom/VIDEO_TS/VTS_17_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_17_0.VOB' -> `./cdrom/VIDEO_TS/VTS_17_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_17_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_17_1.VOB' -> `./cdrom/VIDEO_TS/VTS_17_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_17_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_18_0.BUP' -> `./cdrom/VIDEO_TS/VTS_18_0.BUP'
`/cdrom/VIDEO_TS/VTS_18_0.IFO' -> `./cdrom/VIDEO_TS/VTS_18_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_18_0.VOB' -> `./cdrom/VIDEO_TS/VTS_18_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_18_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_18_1.VOB' -> `./cdrom/VIDEO_TS/VTS_18_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_18_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_19_0.BUP' -> `./cdrom/VIDEO_TS/VTS_19_0.BUP'
`/cdrom/VIDEO_TS/VTS_19_0.IFO' -> `./cdrom/VIDEO_TS/VTS_19_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_19_0.VOB' -> `./cdrom/VIDEO_TS/VTS_19_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_19_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_19_1.VOB' -> `./cdrom/VIDEO_TS/VTS_19_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_19_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_20_0.BUP' -> `./cdrom/VIDEO_TS/VTS_20_0.BUP'
`/cdrom/VIDEO_TS/VTS_20_0.IFO' -> `./cdrom/VIDEO_TS/VTS_20_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_20_0.VOB' -> `./cdrom/VIDEO_TS/VTS_20_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_20_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_20_1.VOB' -> `./cdrom/VIDEO_TS/VTS_20_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_20_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_21_0.BUP' -> `./cdrom/VIDEO_TS/VTS_21_0.BUP'
`/cdrom/VIDEO_TS/VTS_21_0.IFO' -> `./cdrom/VIDEO_TS/VTS_21_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_21_0.VOB' -> `./cdrom/VIDEO_TS/VTS_21_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_21_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_21_1.VOB' -> `./cdrom/VIDEO_TS/VTS_21_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_21_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_22_0.BUP' -> `./cdrom/VIDEO_TS/VTS_22_0.BUP'
`/cdrom/VIDEO_TS/VTS_22_0.IFO' -> `./cdrom/VIDEO_TS/VTS_22_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_22_0.VOB' -> `./cdrom/VIDEO_TS/VTS_22_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_22_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_22_1.VOB' -> `./cdrom/VIDEO_TS/VTS_22_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_22_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_23_0.BUP' -> `./cdrom/VIDEO_TS/VTS_23_0.BUP'
`/cdrom/VIDEO_TS/VTS_23_0.IFO' -> `./cdrom/VIDEO_TS/VTS_23_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_23_0.VOB' -> `./cdrom/VIDEO_TS/VTS_23_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_23_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_23_1.VOB' -> `./cdrom/VIDEO_TS/VTS_23_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_23_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_24_0.BUP' -> `./cdrom/VIDEO_TS/VTS_24_0.BUP'
`/cdrom/VIDEO_TS/VTS_24_0.IFO' -> `./cdrom/VIDEO_TS/VTS_24_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_24_0.VOB' -> `./cdrom/VIDEO_TS/VTS_24_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_24_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_24_1.VOB' -> `./cdrom/VIDEO_TS/VTS_24_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_24_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_25_0.BUP' -> `./cdrom/VIDEO_TS/VTS_25_0.BUP'
`/cdrom/VIDEO_TS/VTS_25_0.IFO' -> `./cdrom/VIDEO_TS/VTS_25_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_25_0.VOB' -> `./cdrom/VIDEO_TS/VTS_25_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_25_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_25_1.VOB' -> `./cdrom/VIDEO_TS/VTS_25_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_25_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_26_0.BUP' -> `./cdrom/VIDEO_TS/VTS_26_0.BUP'
`/cdrom/VIDEO_TS/VTS_26_0.IFO' -> `./cdrom/VIDEO_TS/VTS_26_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_26_0.VOB' -> `./cdrom/VIDEO_TS/VTS_26_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_26_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_26_1.VOB' -> `./cdrom/VIDEO_TS/VTS_26_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_26_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_27_0.BUP' -> `./cdrom/VIDEO_TS/VTS_27_0.BUP'
`/cdrom/VIDEO_TS/VTS_27_0.IFO' -> `./cdrom/VIDEO_TS/VTS_27_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_27_0.VOB' -> `./cdrom/VIDEO_TS/VTS_27_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_27_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_27_1.VOB' -> `./cdrom/VIDEO_TS/VTS_27_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_27_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_28_0.BUP' -> `./cdrom/VIDEO_TS/VTS_28_0.BUP'
`/cdrom/VIDEO_TS/VTS_28_0.IFO' -> `./cdrom/VIDEO_TS/VTS_28_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_28_0.VOB' -> `./cdrom/VIDEO_TS/VTS_28_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_28_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_28_1.VOB' -> `./cdrom/VIDEO_TS/VTS_28_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_28_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_29_0.BUP' -> `./cdrom/VIDEO_TS/VTS_29_0.BUP'
`/cdrom/VIDEO_TS/VTS_29_0.IFO' -> `./cdrom/VIDEO_TS/VTS_29_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_29_0.VOB' -> `./cdrom/VIDEO_TS/VTS_29_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_29_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_29_1.VOB' -> `./cdrom/VIDEO_TS/VTS_29_1.VOB'

cp: reading `/cdrom/VIDEO_TS/VTS_29_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_30_0.BUP' -> `./cdrom/VIDEO_TS/VTS_30_0.BUP'
`/cdrom/VIDEO_TS/VTS_30_0.IFO' -> `./cdrom/VIDEO_TS/VTS_30_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_30_0.VOB' -> `./cdrom/VIDEO_TS/VTS_30_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_30_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_30_1.VOB' -> `./cdrom/VIDEO_TS/VTS_30_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_30_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_31_0.BUP' -> `./cdrom/VIDEO_TS/VTS_31_0.BUP'
`/cdrom/VIDEO_TS/VTS_31_0.IFO' -> `./cdrom/VIDEO_TS/VTS_31_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_31_0.VOB' -> `./cdrom/VIDEO_TS/VTS_31_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_31_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_31_1.VOB' -> `./cdrom/VIDEO_TS/VTS_31_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_31_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_32_0.BUP' -> `./cdrom/VIDEO_TS/VTS_32_0.BUP'
`/cdrom/VIDEO_TS/VTS_32_0.IFO' -> `./cdrom/VIDEO_TS/VTS_32_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_32_0.VOB' -> `./cdrom/VIDEO_TS/VTS_32_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_32_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_32_1.VOB' -> `./cdrom/VIDEO_TS/VTS_32_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_32_1.VOB': Input/output error
[/COLOR]`/cdrom/VIDEO_TS/VTS_33_0.BUP' -> `./cdrom/VIDEO_TS/VTS_33_0.BUP'
`/cdrom/VIDEO_TS/VTS_33_0.IFO' -> `./cdrom/VIDEO_TS/VTS_33_0.IFO'
[COLOR="Red"]`/cdrom/VIDEO_TS/VTS_33_0.VOB' -> `./cdrom/VIDEO_TS/VTS_33_0.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_33_0.VOB': Input/output error
`/cdrom/VIDEO_TS/VTS_33_1.VOB' -> `./cdrom/VIDEO_TS/VTS_33_1.VOB'
cp: reading `/cdrom/VIDEO_TS/VTS_33_1.VOB': Input/output error
[/COLOR]`/cdrom/assets' -> `./cdrom/assets'
`/cdrom/assets/Thumbs.db' -> `./cdrom/assets/Thumbs.db'
`/cdrom/assets/beemovie_bkg.jpg' -> `./cdrom/assets/beemovie_bkg.jpg'
`/cdrom/help.html' -> `./cdrom/help.html'
`/cdrom/images' -> `./cdrom/images'
`/cdrom/images/BEEMovieMain_page_V6_01.gif' -> `./cdrom/images/BEEMovieMain_page_V6_01.gif'
`/cdrom/images/BEEMovieMain_page_V6_02.gif' -> `./cdrom/images/BEEMovieMain_page_V6_02.gif'
`/cdrom/images/BEEMovieMain_page_V6_03-cli.gif' -> `./cdrom/images/BEEMovieMain_page_V6_03-cli.gif'
`/cdrom/images/BEEMovieMain_page_V6_03-ove.gif' -> `./cdrom/images/BEEMovieMain_page_V6_03-ove.gif'
`/cdrom/images/BEEMovieMain_page_V6_03.gif' -> `./cdrom/images/BEEMovieMain_page_V6_03.gif'
`/cdrom/images/BEEMovieMain_page_V6_04-cli.gif' -> `./cdrom/images/BEEMovieMain_page_V6_04-cli.gif'
`/cdrom/images/BEEMovieMain_page_V6_04-ove.gif' -> `./cdrom/images/BEEMovieMain_page_V6_04-ove.gif'
`/cdrom/images/BEEMovieMain_page_V6_04.gif' -> `./cdrom/images/BEEMovieMain_page_V6_04.gif'
`/cdrom/images/BEEMovieMain_page_V6_05-cli.gif' -> `./cdrom/images/BEEMovieMain_page_V6_05-cli.gif'
`/cdrom/images/BEEMovieMain_page_V6_05-ove.gif' -> `./cdrom/images/BEEMovieMain_page_V6_05-ove.gif'
`/cdrom/images/BEEMovieMain_page_V6_05.gif' -> `./cdrom/images/BEEMovieMain_page_V6_05.gif'
`/cdrom/images/BEEMovieMain_page_V6_06.gif' -> `./cdrom/images/BEEMovieMain_page_V6_06.gif'
`/cdrom/images/BEEMovieMain_page_V6_07-cli.gif' -> `./cdrom/images/BEEMovieMain_page_V6_07-cli.gif'
`/cdrom/images/BEEMovieMain_page_V6_07-ove.gif' -> `./cdrom/images/BEEMovieMain_page_V6_07-ove.gif'
`/cdrom/images/BEEMovieMain_page_V6_07.gif' -> `./cdrom/images/BEEMovieMain_page_V6_07.gif'
`/cdrom/images/BEEMovieMain_page_V6_08.gif' -> `./cdrom/images/BEEMovieMain_page_V6_08.gif'
`/cdrom/images/BEEMovieMain_page_V6_09.gif' -> `./cdrom/images/BEEMovieMain_page_V6_09.gif'
`/cdrom/images/BEEMovieMain_page_V6_09a.gif' -> `./cdrom/images/BEEMovieMain_page_V6_09a.gif'
`/cdrom/images/BEEMovieMain_page_V6_09a1.gif' -> `./cdrom/images/BEEMovieMain_page_V6_09a1.gif'
`/cdrom/images/BEEMovieMain_page_V6_09b.gif' -> `./cdrom/images/BEEMovieMain_page_V6_09b.gif'
`/cdrom/images/BEEMovieMain_page_V6_09b1.gif' -> `./cdrom/images/BEEMovieMain_page_V6_09b1.gif'
`/cdrom/images/BEEMovieMain_page_V6_10.gif' -> `./cdrom/images/BEEMovieMain_page_V6_10.gif'
`/cdrom/images/BEEMovieMain_page_V6_11 copy.gif' -> `./cdrom/images/BEEMovieMain_page_V6_11 copy.gif'
`/cdrom/images/BEEMovieMain_page_V6_11.gif' -> `./cdrom/images/BEEMovieMain_page_V6_11.gif'
`/cdrom/images/BEEMovieMain_page_V6_11_rev.gif' -> `./cdrom/images/BEEMovieMain_page_V6_11_rev.gif'
`/cdrom/images/BEEMovieMain_page_V6_12-cli.gif' -> `./cdrom/images/BEEMovieMain_page_V6_12-cli.gif'
`/cdrom/images/BEEMovieMain_page_V6_12-ove.gif' -> `./cdrom/images/BEEMovieMain_page_V6_12-ove.gif'
`/cdrom/images/BEEMovieMain_page_V6_12.gif' -> `./cdrom/images/BEEMovieMain_page_V6_12.gif'
`/cdrom/images/BEEMovieMain_page_V6_13.gif' -> `./cdrom/images/BEEMovieMain_page_V6_13.gif'
`/cdrom/images/BEEMovieMain_page_V6_14.gif' -> `./cdrom/images/BEEMovieMain_page_V6_14.gif'
`/cdrom/images/BEEMovieMain_page_V6_15.gif' -> `./cdrom/images/BEEMovieMain_page_V6_15.gif'
`/cdrom/images/BEEMovieMain_page_V6_16.gif' -> `./cdrom/images/BEEMovieMain_page_V6_16.gif'
`/cdrom/images/BEEMovieMain_page_V6_17.gif' -> `./cdrom/images/BEEMovieMain_page_V6_17.gif'
`/cdrom/images/BEEMovieMain_page_V6_18.gif' -> `./cdrom/images/BEEMovieMain_page_V6_18.gif'
`/cdrom/images/BEEMovieMain_page_V6_19.gif' -> `./cdrom/images/BEEMovieMain_page_V6_19.gif'
`/cdrom/images/beemovie_bkg.jpg' -> `./cdrom/images/beemovie_bkg.jpg'
`/cdrom/images/images' -> `./cdrom/images/images'
`/cdrom/images/images/main_page_FINAL_08.gif' -> `./cdrom/images/images/main_page_FINAL_08.gif'
`/cdrom/images/images/main_page_FINAL_10.gif' -> `./cdrom/images/images/main_page_FINAL_10.gif'
`/cdrom/images/main_page_FINAL_2_06-over.gif' -> `./cdrom/images/main_page_FINAL_2_06-over.gif'
`/cdrom/images/spacer.gif' -> `./cdrom/images/spacer.gif'
`/cdrom/index.html' -> `./cdrom/index.html'
`/cdrom/index_bkg.html' -> `./cdrom/index_bkg.html'
`/cdrom/pdf' -> `./cdrom/pdf'
`/cdrom/pdf/Bee_Printables_CB.pdf' -> `./cdrom/pdf/Bee_Printables_CB.pdf'
`/cdrom/pdf/Bee_Printables_Recipes.pdf' -> `./cdrom/pdf/Bee_Printables_Recipes.pdf'
`/cdrom/pdf/Bee_Printables_Sudoku.pdf' -> `./cdrom/pdf/Bee_Printables_Sudoku.pdf'
`/cdrom/readme.txt' -> `./cdrom/readme.txt'


---

### Post by mc4man on 2008-08-11
You are most likely trying to copy a structured protected disk which among other problems will have a number of unreadable sectors (ranging from a small to very large #)
In these cases any copy command (dd) will fail.
If you wanted to try to dd such a disk you'd use either
> dd if=/dev/[COLOR="Red"]scd1[/COLOR] of=[COLOR="Red"]dvd[/COLOR].iso conv=noerror,sync
dd_rescue -n -b 2048 /dev/[COLOR="Red"]scd0[/COLOR] [COLOR="Red"]movie[/COLOR].iso adjusting what's in red to suit'

Unless there are a small number of unreadable sectors you'll find a dd to be unsuitable for a number of reasons - the time involved could be unreasonable (hours), and the 'rip' will be encrypted and contains errors that may make playback impossible

There is a way to customize vobcopy to rip structure prot. disks, but afterwards you'll still need to fix the intentional structure problems

Your best bet would be to use k9copy - it can deal with and fix alot of s.p. disks though you may need to adjust what and how you rip. (orig. menus, no orig. menus, main movie only, excluding bogus titles ect.ect.) 

K9 can be set to transcode down to dvd5 size or just to rip, ie. set target size above disk size

---

### Post by jadhav333 on 2008-08-11
hi.. u guys/gals have been so helpful.. 

i tried the DVDfab Platinum application through Wine.. and it successfully could copy the files off the dvd onto the harddisk.. also with the compression options to bring a DVD9>DVD5, etc.. 

so i guess that solves it.. 

I only wonder why it couldnot be copied directly through copy paste or cp command or other means??

thanks a lot.. :)

---

### Post by mc4man on 2008-08-11
> I only wonder why it couldnot be copied directly through copy paste or cp command or other means??

solely because of the unreadable sectors (either intentional or due to physical damage)
dd (copy) has no allowance for ignoring read errors and inserting null sectors unless specified in command ('conv=noerror,sync') and in the case of 'dd if=/dev/scd1 of=dvd.iso conv=noerror,sync' no way to have x # of read retries. I'm not sure about the dd_rescue in terms of read retries.

In the case of s.p. read retries are of no value and actually a hindrance.

DVDfab Platinum  should work fine though it does tend to ocassionally bork some rips of disks with no or 'minor' sp.

If there are any playback issues and considering your using wine, then a 'mock strip' in VobBlanker will square things up.
To mock strip you open VobBlanker,  browse to the VIDEO_TS.IFO of your rip, load, ck. use input folder, open file -> Vobs full scan, when done  click process. Afterwards delete the VobBlanker backup in rip folder.

(you can do other useful things with VobBlanker than fix structure.

---

