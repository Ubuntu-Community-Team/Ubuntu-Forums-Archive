---
title: "Cannot Rip CDs"
date: 2017-12-23
forum: Hardware
---

### Post by Kerry Lange on 2017-12-23
I have a strange problem when trying to rip CDs. Ripping starts fine but after one or two songs, ripping stops and I end up with partially complete files.

I've tried a number of programs but all of them behave the same way. The drive spins up and ripping starts. Then, after a minute or two the drive goes silent and ripping stops. There are no error messages or other clues. Currently, I'm using Grip, as it appears to have the features I'm looking for.

Here's the output when I query the drive:

```
  *-cdrom                   
       description: DVD-RAM writer
       product: SDRW-08D2S-U
       vendor: ASUS
       physical id: 0.0.0
       bus info: scsi@10:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: A801
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```

---

### Post by Autodave on 2017-12-24
I use *xfburn *which is probably the best one right now. And I never burn at full speed: I usully take it down a notch or two.

---

### Post by Kerry Lange on 2017-12-24
Thanks Autodave,

I had a look at x/burn, but if I'm not mistaken, it doesn't rip audio files and encode them, as Grip, K3B and others do.

---

### Post by howefield on 2017-12-24
Long time since I ripped a CD but for the command line I'd use abcde or for a GUI application I'd use ripperx.

You don't say what version of Ubuntu you are using but I've tested the above two on 17.10 to make sure they still work.

---

### Post by The Cog on 2017-12-24
As another alternative ripper, I use asunder. But most of these will be using a command-line ripper in the background so you may find that multiple rippers have the same problem. You can use top or htop to see which ripper app is actually doing the ripping. I *think* I remember asunder using cdparanoia in the background.

---

### Post by Doncr on 2018-04-03
abcde wants me to install Postfix, a mail server. Who knew you needed a mail server to rip cd's?

---

### Post by him610 on 2018-04-03
I used Rythmbox a couple of days ago to capture the tracks of three or four CDs on my system with Xubuntu 16.04.4. No issues noted.

---

### Post by Yellow Pasque on 2018-04-04
> **Doncr said:**
> abcde wants me to install Postfix, a mail server. Who knew you needed a mail server to rip cd's?

The purpose of this is to support submissions to the cddb. If you have no interest in that and really don't want to install postfix/bsdmailx, maybe try this:

```
sudo apt-get install libmusicbrainz-discid-perl libdigest-sha-perl libwebservice-musicbrainz-perl imagemagick vorbis-tools
sudo apt-get install --no-install-recommends abcde
```

It probably would be better to ask about abcde here: [https://ubuntuforums.org/showthread.php?t=2257705](https://ubuntuforums.org/showthread.php?t=2257705)

---

