---
title: "show torrent downloads in conky?"
date: 2008-08-16
forum: General Help
---

### Post by mikedemarais on 2008-08-16
hello..
is there anyway i can show how many torrents i am downloading and what the download and upload speeds are in transmission or any other torrent app (i will change to any other app if it works with conky)?

please help.. this would be very cool

---

### Post by tamoneya on 2008-08-16
im not sure how to do it with transmission because it doesnt have much in terms of a command line interface.  If you get a torrent client that allows you to make a commandline call to get the speeds and % complete data you can then just use execi from conky to call the torrent client and get the data into conky.

---

### Post by Lenain777 on 2008-10-18
You can use this code :

```
${color lightgrey}Transmission
$color Seed:
${color #d70752}${exec transmission-remote -l | grep seeding | sed s/seeding\ at//g | sed s/\ GiB/G/g | sed s/\ MiB/M/g | sed s/'('//g | sed s/')'//g | sed s/\ KiB/k/g | sed s/\ \ /\ /g}
$color Download:
${color #d70752}${exec transmission-remote -l | grep -v seeding | sed s/Status\ //g | sed s/Downloading//g | sed s/\ GiB/G/g | sed s/\ MiB/M/g | sed s/'('//g | sed s/')'//g | sed s/\ KiB/k/g | sed s/\ \ /\ /g | sed s/UL\ at/-/g | sed s/done\ in\ //g}
```

It works for me :) Just change the "sed"s to match what you want to see ;)
Have fun!

---

### Post by aeosynth on 2008-12-29
Is there any way to show the progress of individual torrents? Apparently you can with Deluge and rTorrent, how about with Transmission?

---

### Post by Sevmpe on 2008-12-29
You can select an individual torrent with the -t option, e.g. -t3 for the third torrent, and use -i to show the information of the chosen torrent. To know the ETA of the ninth torrent you could type something like:
```
transmission-remote -t9 -i | grep ETA
```

---

### Post by HarshReality on 2009-03-03
Well.. Tried this and wonder if anybody has an updated parse for downloads.. seems it throws up the headers and ETA etc. no matter what grep options are set.. all I'd like to see is:
'nameoffile %complete ETA'

---

### Post by jjgomera on 2009-03-03
Hi
same time ago i tried to output transmission info in conky, i had to use transmission-daemon, because i couldn't connect gtk-cli with daemon, so i left it. 
But if any interested, here is my configuration, the script to parse info:
```
#!/bin/bash

#conky transmission info
#requiere transmission-daemon ejecutandose

case "$1" in

nombre)
	transmission-remote -i |cut -d" " -f2-
	;;

tamaño)
	transmission-remote -l |cut -d")" -f1 |cut -d"(" -f2
	;;

progreso)
	transmission-remote -l |cut -d")" -f2- |cut -d" " -f3 |sed s/%//
	;;

descarga)
	transmission-remote -l |cut -d")" -f2- |cut -d" " -f6
	;;

subida)
	transmission-remote -l |cut -d")" -f2- |cut -d" " -f10
	;;

#estado)
#	 transmission-remote -l |cut -d" " -f6-13 |sed s/downloading/D/ |sed s/at/a/ |sed s/at/a/ |sed s/UL/U/
#	;;

restante)
	transmission-remote -l |cut -d")" -f2- |cut -d" " -f14- |sed s/hour/hora/ |sed s/minutes/minutos/ |sed s/hours/horas/ |sed s/seconds/segundos/ |sed s/days/dias/ |sed s/day/dia/ |sed s/weeks/semanas/ |sed s/week/semana/
	;;

esac
```

the conky code, only text section:

```
TEXT
 
${if_running transmission-daemon}${voffset 10}${font Mac Dingbats:regular:size=14}${color #5da5d3}B${voffset -3}${font Anklepants:regular:size=11}${color #5da5d3} transmission$font$color
${voffset -7}${color #ffd700}${hr 1}$color
${color 888888}${execi 10 /home/jjgomera/configuracion/transmission.sh nombre}
${execi 10 /home/jjgomera/configuracion/transmission.sh progreso}% de ${execi 10 /home/jjgomera/configuracion/transmission.sh tamaño}
${execibar 10 /home/jjgomera/configuracion/transmission.sh progreso}
${font Arrows:size=10}N$font${execi 10 /home/jjgomera/configuracion/transmission.sh descarga}KB/s${alignr 15)}${font Arrows:size=10}S$font${execi 10 /home/jjgomera/configuracion/transmission.sh subida}KB/s
${execi 10 /home/jjgomera/configuracion/transmission.sh restante}
${voffset -5}${color #ffd700}${hr 1}
$endif
```

[IMG]http://img21.imageshack.us/img21/9721/pantallazo3ji8.png[/IMG]

and so showed,i don't remember if work with several simultaneous download, but transmission daemon i didnt like, so i pass to rtorrent, better torrent client

---

### Post by alacrityit on 2009-04-17
jjgomera's script appears to only work for one torrent at a time.  Here's the script I use for multiple torrents.  Make sure you have the web client enabled for this to work.

```
#/bin/bash
#conkytrans.sh

#transmission info in conky
host=acropolis          #host:port

for number in `transmission-remote "$host" -l | awk '{print $1}' | sed '1d'`
do
        torrentinfo=`transmission-remote "$host" -t $number -i`
        name=`echo "$torrentinfo" | grep Name: | sed -e 's/\s\sName:\s//'`
        percent=`echo "$torrentinfo"  | grep Percent | ssed -R 's/\ \ Percent\ Done:\ (\d+.\d+%)/\1/'`
        percentbar=`echo $percent | ssed -R 's/(\d+).\d+%/\1/'`
        if [ "$percentbar" -lt "10" ];then
                percentbar=`echo $percentbar | ssed -R 's/(\d)/0\1/'`
        fi
        total=`echo "$torrentinfo" | grep Total | ssed -R 's/\ \ Total\ size:\ (\d+.\d+\ \w{2}).*/\1/'`
        download=`echo "$torrentinfo" | grep "Download Speed" | sed 's/\ \ Download\ Speed:\ //'`
        eta=`echo "$torrentinfo" | grep ETA | sed 's/\ \ ETA:\ //'`
        echo "$name"
        echo "$percent of $total"
        echo '${execbar echo .'"$percentbar"'}'
        echo "$download"'${alignr 2}'"$eta"
        echo '$hr'
done
```

.conkyrc
```

${execpi 60 /path/to/conkytrans.sh}

```
Here's what it looks like
[IMG]http://brian.addicks.us/stuff/conkytrans.jpg[/IMG]

---

### Post by VCoolio on 2009-10-05
Thank you, this works very well. I had one problem: on transmission-remote -l in a terminal there is also a last line beginning with "Sum:". That was also used in the script and in the conky output, which was nothing but two lines with "of" and ".". To disable, change this line (I added ";$d" in the sed part to ignore also the last line of the output):

```
for number in `transmission-remote -l | awk '{print $1}' | sed '1d;$d'`
```

Maybe this is a specific problem with some versions of transmission (I have 1.73), but if someone experiences the same, this is the solution.

---

### Post by joesnose on 2009-12-20
Great script, i was lookink for something just like this.

I do have a little problem however, all the information displays fine, it is just that my progress bars remain empty. Does anyone know how to fix it?

EDIT: I managed to solve my problem with alot of help from Skones on the IRC conky channel, just incase anyone else has this problem,here is my script.

```
#/bin/sh
#conkytrans.sh

#transmission info in conky
host=127.0.0.1         #host:port

for number in `transmission-remote -l | awk '{print $1}' | sed '1d;$d'`
do
torrentinfo=`transmission-remote "$host" -t $number -i`
name=`echo "$torrentinfo" | grep Name: | sed -e 's/\s\sName:\s//'`
percent=`echo "$torrentinfo"  | grep Percent | ssed -R 's/\ \ Percent\ Done:\ (\d+.\d+%)/\1/'`
percentbar=`echo $percent | ssed -R 's/(\d+).\d+%/\1/'`
if [ "$percentbar" -lt "10" ];then
  percentbar=`echo $percentbar | ssed -R 's/(\d)/0\1/'`
fi
total=`echo "$torrentinfo" | grep Total | ssed -R 's/\ \ Total\ size:\ (\d+.\d+\ \w{2}).*/\1/'`
download=`echo "$torrentinfo" | grep "Download Speed" | sed 's/\ \ Download\ Speed:\ //'`
eta=`echo "$torrentinfo" | grep ETA | sed 's/\ \ ETA:\ //'`

echo "$name"
echo "$percent of $total"
echo '${execbar echo '$percentbar'}'
echo "$download" "$eta"

done
```

---

### Post by lien_meat on 2010-08-19
I found most of the bash-based scripts too slow when I had quite a few torrents running, so I made one in python.  It's specifically made to integrate well into conkycolors generated themes, but will work with any.  You can find it _[here on gnome-look]("http://gnome-look.org/content/show.php/conky+transmission?content=129001")_.

---

### Post by pigimon on 2010-09-18
hi i have used the last code pasted here but my percentage and progressbar stay empty :S any suggestions please :D thank you!

---

### Post by sbjaved on 2012-02-16
Here's a modified version of the bash script posted earlier. This version removes the need for "ssed" to be installed and moves around things a bit.

```
#/bin/sh
#conkytrans.sh

#transmission info in conky
host=127.0.0.1         #host:port

for number in `transmission-remote -l | awk '{print $1}' | sed '1d;$d'`
do
torrentinfo=`transmission-remote "$host" -t $number -i`
name=`echo "$torrentinfo" | grep Name: | sed -e 's/\s\sName:\s//' | fold -w49`
percent=`echo "$torrentinfo"  | grep Percent | sed 's/\ \ Percent\ Done:\ //'`
percentbar=`echo $percent | sed 's/.\{4\}$//'`
total=`echo "$torrentinfo" | grep Total | sed 's/\ \ Total\ size:\ //' | cut -c 1-9`
have=`echo "$torrentinfo" | grep Have | sed 's/\s\sHave:\s//' | cut -c 1-9`
download=`echo "$torrentinfo" | grep "Download Speed" | sed 's/\ \ Download\ Speed:\ //'`
eta=`echo "$torrentinfo" | grep ETA | sed 's/\ \ ETA:\ //' | fold -w18`
state=`echo "$torrentinfo" | grep State | sed -e 's/\s\sState:\s//'`

echo "$name($percent)"
if [ "$state" = "Stopped" ]
then
	echo Paused
else
	echo "$have/$total | $download | $eta"
fi
#echo '${execbar '$percentbar'}' 
echo
done

```

The percentage bar isn't working for me so I commented that bit out. You can re-enable it if you like.

---

