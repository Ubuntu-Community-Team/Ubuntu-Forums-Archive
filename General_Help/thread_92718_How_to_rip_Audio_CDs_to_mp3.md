---
title: "How to rip Audio CDs to mp3 ?"
date: 2005-11-20
forum: General Help
---

### Post by Bachstelze on 2005-11-20
I've tried SoundJuicer but it will only let me rip my CDs to ogg. Any ideas on how to fix it or other programs suggestions ?

---

### Post by Omer on 2005-11-20
First, install *gstreamer0.8-lame*.
Noe go to SoundJuicer, *Edit -> Preferences -> Edit Profiles*.
Create a new profile named MP3.
Edit the profile:
**Gstreamer pipeline**: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 preset=1001 bitrate=128
**File ext**: mp3.
Make sure the profile is set to **Active**.
Restart SJ, and select the new profile MP3 for output format.
*gst-inspect-0.8* lame will give you more info regarding to quality settings

---

### Post by Bachstelze on 2005-11-20
It seems to work but my CD drive is horribly slow (1,2 x)... Is there a way to improve that ?

---

### Post by pickarooney on 2005-11-20
**apt-get install abcde**
then just **abcde**. All the options you need are there.

---

### Post by rama on 2005-11-25
[QUOTE=pickarooney]**apt-get install abcde**
then just **abcde**. All the options you need are there.[/QUOTE]
Forgot to mention that its command line only...

---

### Post by YanH on 2005-11-25
I prefer K3B to Sound Juicer for ripping. Its also good for burning.

---

### Post by kori.mendocino on 2005-11-25
i'd go with goobox for ripping/playing cd's, and with messing up with hdparm's settings for enabling ultra dma for the drives and thus, boosting the speed

---

### Post by jliedeka on 2005-11-25
I'd put my vote in for GRIP.  I've been using it for years.  You have a lot of flexibility with it.

---

### Post by Bachstelze on 2005-11-25
Thanks for all your suggestions guys :) I'm using abcde, which works pretty well.

---

### Post by bionnaki on 2005-11-25
commandline rippers are cool.
I use crip, which is also a commandline,
but it only rips flac & ogg.
so it works out - I only rip flac and ogg :p

---

### Post by nandasunu on 2005-11-26
how to get abcde to rip in mp3 format? I ran it and it seems to default to ogg, and I can see any options to change the format? :confused:

---

### Post by vassie on 2005-11-26
[quote=HymnToLife]Thanks for all your suggestions guys :) I'm using abcde, which works pretty well.[/quote]

HymnToLife
Can you post your .abcde.conf file?
Thanks
Ben

---

### Post by Bachstelze on 2005-11-26
I didn't modify anything in the conf file. To rip as mp3, run "abcde -o mp3"

---

### Post by nandasunu on 2005-11-26
> I didn't modify anything in the conf file. To rip as mp3, run "abcde -o mp3"

I get this error when trying to run that line:

> abcde error: id3v2 is not in your path.

---

### Post by Hairy_Palms on 2005-11-26
do you have lame installed?

if you do it might just be that it doesnt like scousers ;)

---

### Post by Bachstelze on 2005-11-26
This is pretty self-explanatory. Just install the id3v2 package through Synaptic.

---

### Post by nandasunu on 2005-11-26
> This is pretty self-explanatory. Just install the id3v2 package through Synaptic.

and now it works! thanks.

> if you do it might just be that it doesnt like scousers 

easy... just because I live in Liverpool, it doesn't make me a scouser (thank god). I'm unfortunately stuck up here until I finish my degree... :mad:

---

### Post by theclaw on 2005-11-26
Is there anything as good as EAC? Where it goes back and checks each chunk that it has ripped against the original to make sure it's right?

---

### Post by MetalMusicAddict on 2005-11-26
[QUOTE=theclaw]Is there anything as good as EAC? Where it goes back and checks each chunk that it has ripped against the original to make sure it's right?[/QUOTE]
Not that I have found. I do know that if you must EAC will work with WINE. I use Audiograbber with WINE just fine. Mostly because nobody will help me with Grip. :(

---

### Post by vassie on 2005-11-28
abcde depends on id3v2, but does not install it, you will have to install it yourself

```
sudo apt-get install id3v2
```

As for abcde, create a file called .abcde.conf in your home folder and copy this to it

```
# no submitting of cddb info 
NOSUBMIT=y  

# rip to mp3 via lame
MP3ENCODERSYNTAX='lame'

# selection of cd reader
CDROMREADERSYNTAX=cdparanoia 

# zero ifront of tr.no. below 10
PADTRACKS=y

# lame encoder settings
LAMEOPTS="--alt-preset standard"

# Actions to do
ACTIONS=cddb,read,encode,tag,move,clean

# Output dir
OUTPUTDIR='/home/ben/Music'

# temp dir 
WAVOUTPUTDIR='/tmp'

# output type
OUTPUTTYPE=mp3

# naming 
OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'

# naming of multi artist albums (same)
VAOUTPUTFORMAT='${ARTISTFILE}/${ARTISTFILE} - ${ALBUMFILE}/${ARTISTFILE} - ${TRACKNUM} - ${TRACKFILE}'

# don't convert spaces to underscores
mungefilename ()
{
echo "$@" | sed s,:,\ -,g | tr / _ | tr -d \"\?\[:cntrl:\]
}
```

Change OUTPUTDIR to where ever you want your MP3's to go, then all you need to do is type abcde into a terminal

Ben

---

