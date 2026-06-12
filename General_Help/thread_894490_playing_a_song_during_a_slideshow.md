---
title: "playing a song during a slideshow"
date: 2008-08-19
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-08-19
Hi all,
I saw that on a Mac. It was pretty simple to pick a folder with images and then pick a song from somewhere on the computer. The slideshow and the song started together and the time 1 slide was displayed was automatically calculated by *amount_of_images/length_of_music=time_per_image*. Therefor the slideshow ended with the song.
I've always been looking for something like that for Linux. Even if it's not doing that calculation for the slides automatically that would be OK. But I really don't find any app that lets me easily pick some images and a song and then let it play.
I don't want to create a video file, really. Just playing a simple slideshow with a song. Is there anything like that available? So far I am blind, please enlighten me... ;)

I use KDE but I really don't care if it's a KDE, Gnome or whatever else app is.
Ya ya ya, I know, I'm a bad fanboi. ;)
But I just want to get my stuff done. :)

Thanks in advance for any help.

---

### Post by indytim on 2008-08-19
Well it's not Linux :( but rather that "other" ops...

This is what I use to make flash slide shows.  Has the ability to do transitions and include music.  A bit stiff and a little bit buggey but it gets the job done.  As is the case with a lot of Windows apps, it's not free either.

[http://www.flash-slideshow-maker.com/]("http://www.flash-slideshow-maker.com/")

IndyTim

---

### Post by Linux&amp;Gsus on 2008-08-24
Hi,
sorry for the late reply, I had trouble with my computer and had to reinstall from scratch.

So, while it'd be nice to have an app like that, to create a Flash slideshow for websites, it's not what I'm after right now. Besides, Windows apps isn't really an option. While I have an XP installation (dual boot) it's actually only used for checking websites during development process. Besides this app costs ~50$ and you say it's a bit buggy? I mean, no app is bug free but 50 bucks for noticeable buggy software?

Anyways, what I'm after is to show slide shows on my computer. Sorry if I haven't been clear about that. Something like ShowFoto, Gwenview and the like. Just with the ability to add an audio track to the slide show.
A (linux) app that can create Flash slide shows would be nice though.

Cheers.

---

### Post by ezramorris on 2008-09-23
Hi, I wrote a bash script to do this. First install mplayer and feh
```
sudo apt-get install mplayer feh
```

Then choose from one of the following scripts.
For Ubuntu (GNOME):
```
#!/bin/bash

# Show info boxes.
info=true

$info && zenity --title="Slideshow" --info --text="Please select an image folder."
imgdir=$(zenity --title="Image directory" --file-selection --directory) || exit 1
$info && zenity --title="Slideshow" --info --text="Please select a sound file."
sound=$(zenity --title="Music file" --file-selection) || exit 1

cd "$imgdir"
time=$(ffmpeg -i "$sound" 2>&1 |grep Duration |sed 's/  Duration: //' |sed -r "s/\..*//")
hour=$(($(echo $time |cut -d \: -f 1)*3600))
min=$(($(echo $time |cut -d \: -f 2)*60))
sec=$(echo $time |cut -d \: -f 3)
time=$((hour+min+sec))
time=$(($time/$(ls -1 *.jpg *.jpeg *.JPG *.JPEG | wc -l)))

# Feh options
fehopts="-rzF -D $time"

# mplayer options
mplayeropts="-quiet"

function feh_end {
  # Allow mplayer to finish.
  sleep 2
  killall mplayer
}

feh $fehopts *.jpg *.jpeg *.JPG *.JPEG && feh_end &
mplayer $mplayeropts "$sound"
killall feh
```

For Kubuntu (KDE):
```
#!/bin/bash

# Show info boxes.
info=true

$info && kdialog --title "Slideshow" --msgbox "Please select an image folder."
imgdir=$(kdialog --title "Image directory" --getexistingdirectory .) || exit 1
$info && kdialog --title "Slideshow" --msgbox "Please select a sound file."
sound=$(kdialog --title "Music file" --getopenfilename .) || exit 1

cd "$imgdir"
time=$(ffmpeg -i "$sound" 2>&1 |grep Duration |sed 's/  Duration: //' |sed -r "s/\..*//")
hour=$(($(echo $time |cut -d \: -f 1)*3600))
min=$(($(echo $time |cut -d \: -f 2)*60))
sec=$(echo $time |cut -d \: -f 3)
time=$((hour+min+sec))
time=$(($time/$(ls -1 *.jpg *.jpeg *.JPG *.JPEG | wc -l)))

# Feh options
fehopts="-rzF -D $time"

# mplayer options
mplayeropts="-quiet"

function feh_end {
  # Allow mplayer to finish.
  sleep 2
  killall mplayer
}

feh $fehopts *.jpg *.jpeg *.JPG *.JPEG && feh_end &
mplayer $mplayeropts "$sound"
killall feh
```

Hope this helps.

Edit: Oops, I didn't read the question properly. Now updated to time the photos to the music.

---

