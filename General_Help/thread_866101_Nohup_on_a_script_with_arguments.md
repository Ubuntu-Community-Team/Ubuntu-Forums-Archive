---
title: "Nohup on a script with arguments?"
date: 2008-07-21
forum: General Help
---

### Post by Nuvious on 2008-07-21
I'm trying to nohup a script of mine and I'm having problems.

My script is a time-lapse script I wrote so I could film the sunrise and sunset every day:

```
declare -i hour
declare -i currHour
declare device
declare tag
declare vidtag
declare -i delay
declare -i max

function runTimeLapse {
	currHour=`date +%k`

	while [ $currHour -ne $hour ]; do
		tag=`date +%Y%m%d%H%M%S`
		setpwc -d $device -x -f 10
		vgrabbj -d $device -S -i vga -o png -f $tag.png 1>>grab.log 2>>grab.log
		echo "$tag"
		sleep "$delay"s
		currHour=`date +%k`
	done
}

hour=$3
delay=$2
device=$1

while [ true ]; do
	vidtag=`date +%Y%m%d`
	mkdir $vidtag
	cd $vidtag
	runTimeLapse
	for currFile in `du *.png -h | grep ^0 | gawk '{split($0,a," ");print a[2]}'`; do
		rm $currFile
	done
	mencoder "mf://*.png" -mf fps=15 -o $vidtag.avi -ovc lavc
	tar -czf $vidtag.tar.gz $vidtag.avi
	rm *.png
	cd ../
done

```

The script basically takes three arguments: the webcam device name, the "rough" delay between taking an exposure, and the hour at which to compile the video and start the next.  Though this is version 0.000000000001 on the way to version 1.0, I still would like to run it to get pretty sunrises and sunsets :).  The script runs fine when I'm logged in and using a console, but I want to nohup it so I can log out of my terminal while it's working.  This is the error I get when I run:

```
nohup nice ./DailySunrise.sh /dev/video0 30 0
```

> ./DailySunrise.sh: 1: declare: not found
./DailySunrise.sh: 2: declare: not found
./DailySunrise.sh: 3: declare: not found
./DailySunrise.sh: 4: declare: not found
./DailySunrise.sh: 5: declare: not found
./DailySunrise.sh: 6: declare: not found
./DailySunrise.sh: 7: declare: not found
./DailySunrise.sh: 9: function: not found
[: 19: -ne: argument expected
./DailySunrise.sh: 20: Syntax error: "}" unexpected


I've tried various solutions including writing an auxiliary script to run the arguments, but none of my solutions seem to get around this problem.  Any ideas?  Thanks in advance for any replies!

---

### Post by Vivaldi Gloria on 2008-07-21
I don't understand the point of including "nice" without any arguments in your command

```
nohup nice ./DailySunrise.sh /dev/video0 30 0
```

Try:

```
(nohup ./DailySunrise.sh /dev/video0 30 0&)
```

Or use screen:

```
screen
./DailySunrise.sh /dev/video0 30 0
```

See these for more info on screen:

[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)
[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://aperiodic.net/screen/quick_reference](http://aperiodic.net/screen/quick_reference)

---

