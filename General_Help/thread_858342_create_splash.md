---
title: "create splash"
date: 2008-07-13
forum: General Help
---

### Post by 1234 on 2008-07-13
how can i create my own startup splash for ubuntu and the one  running from usb using syslinux.

---

### Post by dexter.deepak on 2008-07-13
you can try this script for ubuntu, place it in your ~/.gnome2/nautilus-scripts folders and give a+x permissions...you will get an option to make any image as splash, just from the right-click menu.
```
#!/bin/bash
SCRIPT_VERSION=1.03
FNAME="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" 
file=$@
# everything after last '/'
basename=${file%.*}
ext=".so"
OUTFILE=${basename}${ext}

`zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --info --text="This will complie a USplash in current folder called $OUTFILE you can then load this file into Startup Manager.  Enjoy, TheeMahn" --title="USplash Maker"`;
##Check for zenity
if [ ! -e "/usr/bin/zenity" ]; then
	gksudo apt-get install -y --force-yes zenity
fi

update() {
 wget -O /tmp/MakeUsplash http://ubuntusoftware.info/scripts/MakeUsplash >/dev/null 2>&1

#Verify it did download it
RESULTS_SIZE=`stat -c %s /tmp/MakeUsplash`
if [ "$RESULTS_SIZE" = 0 ]
then
    zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --info --text='It is suggested to re-run the script, the server may be under a heavy load.  If the message persists, please verify you have an internet connection, the server is online &amp; try again.  Please refer to UbuntuSoftware Forum for further info.' --title="UbuntuSoftware USplashMaker";
    exit 0
fi
#Version check script
 REMOTE_VERSION=`grep SCRIPT_VERSION /tmp/MakeUsplash |head -n1 |sed 's/.*=//'`
 if [ "$REMOTE_VERSION" != "$SCRIPT_VERSION" ]; then
  if [[ -n $DIALOG ]]
  then
   dialog --yesno "Newer version of USplash Maker script has been found\n\nDo you wish to install it?" 0 0
   DIALOG_EXIT_CODE=$?
   if [[ $DIALOG_EXIT_CODE = 0 ]]
   then
    cp /tmp/MakeUsplash ~/.gnome2/nautilus-scripts/
    echo "USplash Maker script has been updated to v $REMOTE_VERSION"
    echo "Please re-run the script"
    zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --info --text='Newer version of script detected '$REMOTE_VERSION'.  It has been upgraded please re-run script.' --title="USplash Maker script";
    exit
   fi
  else
   cp /tmp/MakeUsplash /.gnome2/nautilus-scripts/
   echo "Newer version detected: $REMOTE_VERSION"
   zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --info --text='Newer version of script detected '$REMOTE_VERSION'.  It has been upgraded please re-run script.' --title="USplash Maker script";
   exit
  fi
 fi
 rm /tmp/MakeUsplash 2>/dev/null
}
update
PROGRESS=0
#FNAME=$@
 
#Resolution Subroutines
Res1(){
#cd $
convert -colors 256 $FNAME -resize "640X400!" -quality 100 -strip WorkInProgress/usplash_640_400.png | zenity --width=600 --height=100 --progress --pulsate --auto-close --title "Processing @ 640 X 400..."
# Palleting of progressbar - Thanks red_team316
convert WorkInProgress/usplash_640_400.png WorkInProgress/throbber_back_640_400.png WorkInProgress/throbber_fore_640_400.png -append WorkInProgress/append.png
convert WorkInProgress/append.png +dither -colors 256 WorkInProgress/paletted.png
convert WorkInProgress/paletted.png -crop 640x400+0+0! WorkInProgress/usplash_640_400.png
convert WorkInProgress/paletted.png -crop 216x8+0+400! WorkInProgress/throbber_back_640_400.png
convert WorkInProgress/paletted.png -crop 216x8+0+408! WorkInProgress/throbber_fore_640_400.png
}

Res2(){
#640X480
#cd $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
convert -colors 256 $FNAME -resize "640X480!" -quality 100 -strip WorkInProgress/usplash_640_480.png | zenity --width=600 --height=100 --progress --pulsate --auto-close --title "Processing @ 640 X 480..."
convert WorkInProgress/usplash_640_480.png WorkInProgress/throbber_back_640_480.png WorkInProgress/throbber_fore_640_480.png -append WorkInProgress/append.png
convert WorkInProgress/append.png +dither -colors 256 WorkInProgress/paletted.png
convert WorkInProgress/paletted.png -crop 640x480+0+0! WorkInProgress/usplash_640_480.png
convert WorkInProgress/paletted.png -crop 216x8+0+480! WorkInProgress/throbber_back_640_480.png
convert WorkInProgress/paletted.png -crop 216x8+0+488! WorkInProgress/throbber_fore_640_480.png
}

Res3(){
#800X600
#cd $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
convert -colors 256 $FNAME -resize "800X600!" -quality 100 -strip WorkInProgress/usplash_800_600.png | zenity --width=600 --height=100 --progress --pulsate --auto-close --title "Processing @ 800 X 600..."
convert WorkInProgress/usplash_800_600.png WorkInProgress/throbber_back_800_600.png WorkInProgress/throbber_fore_800_600.png -append WorkInProgress/append.png
convert WorkInProgress/append.png +dither -colors 256 WorkInProgress/paletted.png
convert WorkInProgress/paletted.png -crop 800x600+0+0! WorkInProgress/usplash_800_600.png
convert WorkInProgress/paletted.png -crop 216x8+0+600! WorkInProgress/throbber_back_800_600.png
convert WorkInProgress/paletted.png -crop 216x8+0+608! WorkInProgress/throbber_fore_800_600.png
}

Res4(){
#1024 X 768
convert -colors 256 $FNAME -resize "1024X768!" -quality 100 -strip WorkInProgress/usplash_1024_768.png | zenity --width=600 --height=100 --progress --pulsate --auto-close --title "Processing @ 1024 X 768..."
convert WorkInProgress/usplash_1024_768.png WorkInProgress/throbber_back_1024_768.png WorkInProgress/throbber_fore_1024_768.png -append WorkInProgress/append.png
convert WorkInProgress/append.png +dither -colors 256 WorkInProgress/paletted.png
convert WorkInProgress/paletted.png -crop 1024x768+0+0! WorkInProgress/usplash_1024_768.png
convert WorkInProgress/paletted.png -crop 216x8+0+768! WorkInProgress/throbber_back_1024_768.png
convert WorkInProgress/paletted.png -crop 216x8+0+776! WorkInProgress/throbber_fore_1024_768.png
}

Res5(){
#1280X1024
convert -colors 256 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS -resize "1280X1024!" -quality 100 -strip WorkInProgress/usplash_1280_1024.png | zenity --width=600 --height=100 --progress --pulsate --auto-close --title "Processing @ 1280 X 1024..."
convert WorkInProgress/usplash_1280_1024.png WorkInProgress/throbber_back_1280_1024.png WorkInProgress/throbber_fore_1280_1024.png -append WorkInProgress/append.png
convert WorkInProgress/append.png +dither -colors 256 WorkInProgress/paletted.png
convert WorkInProgress/paletted.png -crop 1280x1024+0+0! WorkInProgress/usplash_1280_1024.png
convert WorkInProgress/paletted.png -crop 216x8+0+1024! WorkInProgress/throbber_back_1280_1024.png
convert WorkInProgress/paletted.png -crop 216x8+0+1032! WorkInProgress/throbber_fore_1280_1024.png
}

#C Code Subroutines
Header(){
#Grab Throbbers, fonts & C code
cd WorkInProgress
wget http://ubuntusoftware.info/scripts/USplash/USplash.tar.gz
tar xfv USplash.tar.gz
cd ..
}

# Dialog box to choose USplash's size(s)
# Begin interaction with end user
`zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --info --text="This will complie a USplash in current folder called $OUTFILE you can then load this file into Startup Manager (SUM).  Enjoy, TheeMahn" --title="TUM - TheeMahns USplash Maker"`;
SIZE="";
SIZE="$(zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png  --width=500 --height=280 --title "TUM - TheeMahns USplash Maker" --text "Choose the Usplash resolutions to be compiled." --list --checklist --column "Select" --column "Resolution" true '600X400' true '640X480' true '800X600' true '1024X768' true '1280X1024')";
echo $SIZE
if [ "${SIZE}" == "" ]; then   
zenity --error --text="Resolution not defined by user.  Please choose a size to use. "
exit 0
fi
n=0
if echo "$SIZE" | grep "600X400" ; then
n=$(($n + 1))
echo -n "$n "
fi
if echo "$SIZE" | grep "640X480" ; then
n=$(($n + 1))
echo -n "$n "
fi
if echo "$SIZE" | grep "800X600" ; then
n=$(($n + 1))
echo -n "$n "
fi
if echo "$SIZE" | grep "1024X768" ; then
n=$(($n + 1))
echo -n "$n "
fi
if echo "$SIZE" | grep "1280X1024" ; then
n=$(($n + 1))
echo -n "$n "
fi
PROGRESS=0
TOTAL=$((100 / $n))
echo $TOTAL
mkdir -p WorkInProgress
Header
if echo "$SIZE" | grep "600X400" ; then
Res1
fi
if echo "$SIZE" | grep "640X480" ; then
Res2
fi
if echo "$SIZE" | grep "800X600" ; then
Res3
fi
if echo "$SIZE" | grep "1024X768" ; then
Res4
fi
if echo "$SIZE" | grep "1280X1024" ; then
Res5
fi
cd WorkInProgress
make | zenity --width=600 --height=100 --progress --pulsate --auto-close --title "Compiling USplash"
mv usplash-theme-ubuntu.so ../$OUTFILE
cd ..
#Clean up
rm -R WorkInProgress
exit 0
```

P.S : this script isnt developed by me...someone gave it to me a while back.

---

### Post by x0x on 2008-12-06
this script doesnt work..

---

