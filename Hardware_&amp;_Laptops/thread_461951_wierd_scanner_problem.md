---
title: "wierd scanner problem"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by ColPop on 2007-06-02
Hi, I'm a new user and so far so good, except this one problem with my scanner. it's a CanoScan N670U, and all the online list say it is compatible and I did manage to get it going without too much hassle.
However, I'm using XSane and it finds the scanner, but when I click scan it doesn't seem to connect to the scanner, nothing happens. It goes through the motions on screen (i.e. %scanned) but the scanner doesn't actually do anything. Once it thinks it has finished scanning it gives a blank document as the scanned picture. I played around a bit and eventually got it going, but the next time I tried it didn't work again. I soon realised that the only time it scanned was if I pressed scan straight after the program booted, i.e. when the scanner was warming up. I thought it might be a software problem, so I installed Kooka, but I encountered exactly the same problem.
Although I can scan it is annoying to have to reboot the program every time I need to scan something different! Thanks

---

### Post by maino82 on 2007-06-03
I have a similar problem with the n650u. I think it has something to do with the way Feisty handles USB ports when they're not active. In any event, it worked just fine from the command line "scanimage" command, so I wrote up a little bash script to do the job for me. It can't use all the options, but the most common ones are there like x and y dimenstions, file type, color depth and mode (plus some others). To try it out just copy and paste it into a file and then 

```
$ chmod 0777 SCRIPT_NAME
$ ./SCRIPT_NAME -n OUTPUT_FILE
```

I'm a bash scripting n00b, so hopefully this won't explode on you, but I've been using it for awhile now and it seems to work alright. Here's the code:

```
#!/bin/bash
#
# default values:
# scanimage -x 210 -y 290 --depth 8 -l 0 -t 0 --brightness 0 --contrast 0 --resolution 400 --mode Color -p > $filename.tiff
# scanimage -x $x -y $y --depth $d -l $l -t $t --brightness $b --contrast $c --resolution $r --mode $m $p > $filename.$f

#===========================
#Functions for the script
#===========================
function pause {
	echo -n Hit Enter to continue...
	read
	}

function error {
	echo $SCRIPT "encountered an error in '$1':"
	echo "	Wrong input. Type --help for help."
	pause
	exit 192
	}

function check_scanners {
	scanners=`scanimage -L | grep 'No scanners'`

	if [ -n "$scanners" ]
	then
        	echo "No scanners detected. Please make sure that the scanner is connected and turned on and try again."
        	pause
        	exit 192
	fi
	}

function scan {
	check_scanners

	echo "Scanning image. Please wait, this may take awhile..."
	echo "	scanimage -x $x -y $y --depth $d -l $l -t $t --brightness $b --format=$f --contrast $c --resolution $r --mode $m $p > $filename.$f"
	scanimage -x $x -y $y --depth $d -l $l -t $t --brightness $b --format=$f --contrast $c --resolution $r --mode $m $p > $filename.$f && echo "Scan complete. File saved to $filename.$f"
	pause
	}

#===========================
# Define our default values
#===========================
x=210
y=290
m=Color
r=400
l=0
t=0
b=0
c=0
d=8
p=-p
f=tiff

declare -rx SCRIPT=${0##*/}

#===========================
# Check for parameters
#===========================
if [ $# -eq 0 ] ; then
	error "parameters"
fi

while [ $# -gt 0 ] ; do
	case $1 in
	-h | --help) #show help
		echo "Usage: $SCRIPT [-h|--help][-x (0-210)][-y (0-290)][-r (50-1200)][-m (Color|Gray|Lineart)][-d (8|14)][-l (0-x)][-t (0-y)][-b (-100-100)][-c (-100-100)][-p (yes|no)][-f (tiff|pnm)] -n filename"
		echo "	-h,--help : 	this help file"
		echo "	-x : 		x size in mm [0-210]"
		echo "	-y : 		y size in mm [0-290]"
		echo "	-r : 		resolution [50-1200]"
		echo "	-m : 		mode [Color|Gray|Lineart]"
		echo "	-d : 		depth [8|14]"
		echo "	-l : 		left start point [0-x]"
		echo "	-t : 		top start point [0-y]"
		echo "	-b : 		brightness [-100 to 100]"
		echo "	-c : 		contrast [-100 to 100]"
		echo "	-p : 		print progress [yes|no]"
		echo "	-f : 		format [tiff|pnm]"
		echo "	filename :	output filename (extension not required)"
		echo "Defaults:"
		echo "	-x 210 -y 290 -r 400 -m Color -d 8 -l 0 -t 0 -b 0 -c 0 -p yes -f tiff"   
		exit 0
		;;
	-x) shift
		if [[ 0 -le $1 && $1 -le 210 ]]
		then
			x=$1
		else
			error $1
		fi
		;;
	-y) shift
                if [[ 0 -le $1 && $1 -le 290 ]]
		then
                        y=$1
                else
			error $1
                fi
		;;
	-r) shift
                if [[ 50 -le $1 && $1 -le 1200 ]]
		then
                        r=$1
                else
			error $1
                fi
		;;
	-m) shift
		if [[ $1 = Color || $1 = Gray || $1 = Lineart ]]
		then
			m=$1
		else
			error $1
		fi
		;;
	-d) shift
		if [[ $1 -eq 8 || $1 -eq 14 ]]
		then
			d=$1
		else
			error $1
		fi
		;;
	-l) shift
		if [[ 0 -le $1 && $1 -le $x ]]
		then
			l=$1
		else
			error $1
		fi
		;;
	-t) shift
                if [[ 0 -le $1 && $1 -le $y ]]
		then
                        t=$1
                else
			error $1
		fi
		;;
	-b) shift
		if [[ -100 -le $1 && $1 -le 100 ]]
		then
			b=$1
		else
			error $1
		fi
		;;
	-c) shift
                if [[ -100 -le $1 && $1 -le 100 ]]
		then
                        c=$1
                else
			error $1
		fi
		;;
	-p) shift
		if [ $1 = "yes" ]
		then
			p=-p
		elif [ $1 = "no" ]
		then
			p=
		else
			error $1
		fi	
		;;
	-f) shift
		if [[ $1 = "pnm" || $1 = "tiff" ]]
		then
			f=$1
		else
			error $1
		fi
		;;
	-n) shift
		if [ -n $1 ]
		then
			filename=$1
		else
			echo "Required filename input missing"
			exit 192
		fi
		;;
	-*) error $1;;
	*) error $1;;
	esac
	shift
done

#===========================
# Check that we've given a 
# proper filename
#===========================
if [ -n $filename ] 
then
	scan
else
	echo "Required filename input missing"
	exit 192
fi

exit 0
```

Yes, it's somewhat redundant since the scanimage program takes care of all of this, but this way you can change the defaults in the program to the ones you use most often and just run ./scan.sh -n output.

---

### Post by Detonate on 2007-06-04
I have the same scanner (670n) and the same problem.  If I run scanimage at the CLI it works.  But it does not work in Xsane or in Kooka.  Scanner never actually runs, but eventually the program will show a black page.  This scanner works perfectly in PCLinuxOS-2007 on the same computer using Xsane.

---

### Post by Detonate on 2007-06-04
OK, after some serious searching I found out that this is a known bug.

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

---

### Post by Detonate on 2007-06-04
OK, I found an easy workaround that works for me, I have tried it with both Kooka and Xsane.

Install scanbuttond.

```
sudo aptitude install scanbuttond
```

Start scanbuttond with the following value at the command line.

```
scanbuttond -r 1000000
```

Now Kooka and Xsane will work.

You'll probably have to rerun this after every boot.

You can read more about this workaround at the launchpad site I posted above, this works for my N670u but other scanners might need some tweaking of the scanbuttond program.

---

