---
title: "What about archos gmini 402 ?"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by frodon on 2006-01-04
Hi,

i'm going to buy an [archos gmini 402]("http://www.amazon.com/gp/product/B000AA7MQA/qid=1136379930/sr=8-1/ref=pd_bbs_1/002-8449520-2243246?n=507846&s=electronics&v=glance") and i would like to know if there are some of you here who use it and how they are happy with.
Is there any problems with this player and ubuntu ?
Is there a good software to convert the divx in the good format if it's needed ?

Thanks for any kind of answer.

---

### Post by frodon on 2006-01-06
nobody use it ?

---

### Post by kblood on 2006-06-14
Sorry, I hadn't seen this thread!

I have it and love it! It works as an external USB hard drive, so it works beautifully with Ubuntu!

I have somewhere a script that helps a lot to convert movies quickly to watch them in it.

Definitely recommended! Great little player!

PS: Here is the script:
```
#!/bin/bash
# usage:  divx2gmini <file>
#
# Author: Nick Van Helleputte
# It works for me, no guarantee that it will work for you :)

VERSION=0.3

#define colors
bold=`tput bold;tput setaf 4`
offbold=`tput sgr0`
red=`tput setaf 1`
green=`tput setaf 2`
yellow=`tput setaf 3`
blue=`tput setaf 4`
purlple=`tput setaf 5`
cyan=`tput setaf 6`
white=`tput bold;tput setaf 7`

if ! [ -e "$1" ]; then
    cat <<EOF
${green}divx2gmini-$VERSION${offbold} by Nick Van Helleputte.
A bash script to re-encode video to a format appropriate for the 
Archos Gmini 400. It encodes to Xvid video and CBR mp3 audio.

${bold}Overview:${offbold}
    - The script will ask to generate a 5 min. test sample you can 
      quickly copy to your Gmini to see if any reencoding is needed.
    - The script will give you the option to only reencode audio.
      (since most of the time only the audio needs to be reencoded)
    - If video will also be reencoded, the script will ask to use 
      2-pass encoding or not.
    - If you want subtitles to be rendered in the final result, just 
      place the subtitle file in the same directory as the video and
      give it the same name.
      (e.g. ${white}~jack/movies/video1.avi${offbold} and ${white}~jack/movies/video1.srt${offbold})

${bold}Requirements:${offbold}
    - transcode
    - mplayer & mencoder
    - xvid and lame libraries

${bold}usage:${offbold}
    ${white}dixv2gmini <videofile>${offbold}
EOF
    exit
fi

#define some vars
DIR=`pwd`
TEMPFOLDER=/tmp/divx2gmini-$RANDOM
FILE=$1
if [ "$1" == "`basename \"$1\"`" ]; then
	FILE="$DIR/$1"
fi
OUTPUT="${FILE%.avi}_gmini.avi"
CLIP="${FILE%.avi}_clip.avi"
mkdir $TEMPFOLDER
cd $TEMPFOLDER

#get info from source
mplayer -frames 0 -identify "$FILE" > $TEMPFOLDER/info 2>/dev/null

# Test sample
echo "${bold}Generate 5min. test sample?${offbold} (output in ${green}$CLIP)${offbold} (y/n)"
read TEST
if [ $TEST = "y" ]; then
    #zoek de lengte van de input
    ID_LENGTH=`grep LENGTH $TEMPFOLDER/info`
    LENGTH=${ID_LENGTH#ID_LENGTH=}
    
    #bereken start en einde van de clip
    let START=$LENGTH/$LENGTH
    let STOP=$START+300

    mencoder -o "$CLIP" -oac copy -ovc copy -ss $START -endpos $STOP "$FILE"
    echo "${red}Done! 5 min. test sample can by found in ${green}$CLIP.${offbold}"
    #clean up and exit
    rm $TEMPFOLDER/*
    rmdir $TEMPFOLDER
    cd $DIR
    exit
fi

# Audio
echo "${bold}Re-encode only audio?${offbold} (output in ${green}$OUTPUT)${offbold} (y/n)"
read AUDIO

#bepaal audio source bitrate?
ABITRATE=`grep AUDIO_BITRATE $TEMPFOLDER/info`
ABITRATE=${ABITRATE#ID_AUDIO_BITRATE=}
let ABITRATE=$ABITRATE/1000

#bepaal audio target bitrate
echo "${bold}Audio bitrate in kbps?${offbold} (source = ${green}$ABITRATE${offbold})"
read ABITRATE

AUDIORATE=$ABITRATE,0,5,0

#encode only audio
if [ $AUDIO = "y" ]; then
    transcode -i "$FILE" -N 0x55 -P 1 -b $AUDIORATE -o "$OUTPUT"
    echo "${red}Done! Audio encoded succesfully.${offbold}"

    #clean up and exit
    rm $TEMPFOLDER/*
    rmdir $TEMPFOLDER
    cd $DIR
    exit
fi

# Video
echo "${bold}Use 2-pass video encoding?${offbold} (output in ${green}$OUTPUT)${offbold} (y/n)"
read TWOPASS
TWOPASSFLAG=""

#bepaal video source bitrate?
VBITRATE=`grep VIDEO_BITRATE $TEMPFOLDER/info`
VBITRATE=${VBITRATE#ID_VIDEO_BITRATE=}
let VBITRATE=$VBITRATE/1000

#bepaal video target bitrate    
echo "${bold}Video bitrate in kbps?${offbold} (source = ${green}$VBITRATE${offbold})"
read MAXRATE

#encode video
if [ $TWOPASS = "y" ]; then
    # first pass encoding
    # no audio processing
    # no video output
    transcode -i "$FILE" -V -x mplayer -y xvid4,null \
	-R1 -o /dev/null

    #set twopassflag
    TWOPASSFLAG="-R2"
fi

#encode video
# -i          input
# -V          use YV12/I420 as internal video codec
# -x mplayer  use mplayer to render video/audio
# -y xvid     encode to xvid
# -N 0x55     encode audio to CBR mp3
# -b          audio bitrate
# -o          output
# -w          video bitrate
transcode -i "$FILE" -V -x mplayer -y xvid4 \
  $TWOPASSFLAG -N 0x55 -b $AUDIORATE -o "$OUTPUT" -w $MAXRATE 

echo "${red}Done! Audio and video encoded succesfully.${offbold}"

# clean up and exit
rm $TEMPFOLDER/*
rmdir $TEMPFOLDER
cd $DIR

exit
```

---

### Post by annda on 2006-07-10
i know this thread is stale by now, but i thought maybe someone was still considering buying the gmini. so here are my 2 cents:

i've watched many different avis on the gmini (not on the display of course, but thru the av-out) and never needed to convert/transcode anything. ok, it won't play avi files with encoded ac3, so you might occasionally have to convert the audio.
 
apart from that, highly recommended. no issues with linux, as it can easily be set to usb drive mode (in addition to 'windows media device').

---

