---
title: "Big cpu draw"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by Connollyir on 2005-12-31
When I copy files from cd or dvd to my hard disk I get 100% cpu usage in system monitor and it slows my computer down significantly - what can I do about it?

---

### Post by ninotob on 2005-12-31
You want to use "nice"

eg:

nice -n 10 cp this there

The range is -20 to 19.  -20 is highest priority, 19 is lowest.

Note, I've not ever had to nice anything, I just pulled that info out of the man page.

---

### Post by Connollyir on 2006-01-01
[QUOTE=ninotob]You want to use "nice"

eg:

nice -n 10 cp this there

The range is -20 to 19.  -20 is highest priority, 19 is lowest.

Note, I've not ever had to nice anything, I just pulled that info out of the man page.[/QUOTE]

Is nicing that uncommon? If so I should look elsewhere in my system for problems first before I try this Correct? But where would I look?

-Ian

---

### Post by ninotob on 2006-01-01
[QUOTE=Connollyir]Is nicing that uncommon? If so I should look elsewhere in my system for problems first before I try this Correct? But where would I look?

-Ian[/QUOTE]

I rarely transfer large files off discs to my HD -- perhaps even never.  You're system may be behaving completely normally so I'd say try nice -- that's what it's for.

Maybe you should check whether DMA is turned on for your disc -- the following command is informational only, it doesn't do anything to your system:

hdparm /dev/hdc

will give you info about your disc (if you have two discs, then the second would be /dev/hdd).  Note, there is an error message "HDIO_GETGEO failed: Invalid argument" which I googled on once upon a time:  [http://ubuntuforums.org/archive/index.php/t-34151.html](http://ubuntuforums.org/archive/index.php/t-34151.html)  Scroll all the way down for the answer.  Apparently, it's just trying to find out the size of the disc and can't because there is no disc loaded if you do this on an empty drive.

If you don't have DMA turned on for your disc, you can do that like this (this actually does the turning on of DMA):

sudo hdparm -d1 /dev/hdc

to turn DMA off:

sudo hdparm -d0 /dev/hdc

Note, that is -d<zero> (not "oh")

Try that and see if it helps.  If not, embrace nice.

---

### Post by Connollyir on 2006-01-01
[QUOTE=ninotob]I rarely transfer large files off discs to my HD -- perhaps even never.  You're system may be behaving completely normally so I'd say try nice -- that's what it's for.

Maybe you should check whether DMA is turned on for your disc -- the following command is informational only, it doesn't do anything to your system:

hdparm /dev/hdc

will give you info about your disc (if you have two discs, then the second would be /dev/hdd).  Note, there is an error message "HDIO_GETGEO failed: Invalid argument" which I googled on once upon a time:  [http://ubuntuforums.org/archive/index.php/t-34151.html](http://ubuntuforums.org/archive/index.php/t-34151.html)  Scroll all the way down for the answer.  Apparently, it's just trying to find out the size of the disc and can't because there is no disc loaded if you do this on an empty drive.

If you don't have DMA turned on for your disc, you can do that like this (this actually does the turning on of DMA):

sudo hdparm -d1 /dev/hdc

to turn DMA off:

sudo hdparm -d0 /dev/hdc

Note, that is -d<zero> (not "oh")

Try that and see if it helps.  If not, embrace nice.[/QUOTE]

Well I checked all my disks - I have 3 with one set in RAID - and all had DMA enabled. So I'm going to try nice but I am unclear about your command. When you say "nice -n 10 cp this there", by "this there" do you mean "filename" "location"? And wouldn't that only be a temporary fix? I would like to set the nice level of the copying process from /dev/cdrom to 10 as a standard thing if that would improve the performance of my machine.

The weird thing is I am using a decent machine - AMD 64 3200+ with 1 GB of low latency ram (although I forget the timing) and on several previous installations of Ubuntu on the same machine the same problem happened several times and didn't happen in other installations.

---

### Post by ninotob on 2006-01-01
Not sure why it would happen.

First, you're right about "this there".  That would be something like 

/path/to/file.txt /path/to/where/you/want/to/copy/it/to

Probably the simplest thing to do so that other copy commands aren't limited, is to make an alias, e.g.

alias cdcp='nice -n 10 cp'

Test it out -- I'm not 100% certain that you can string together two commands like that in an alias, though it does work for me copying a very small test file -- in other words, I can't see the "nice" effect, but the copy works.  You would use this by typing:

cdcp this there

(using my original shorthand)

If it doesn't make a difference, you could make a script:

```

#!/bin/bash
THIS=$1
THERE=$2
nice -n 10 cp $THIS $THERE


```

Save that as file named "cdcp".  
Chmod 770 cdcp
copy it to a directory in your path with sudo

To see the directories in your path, type:

echo $PATH

probably /usr/local/bin would be a decent choice.  To use it, you'd just type:
cdcp <file_path> <destination_path>

---

### Post by ninotob on 2006-01-01
Note -- there was an omission in my script which I fixed -- best hit reload in case you are viewing a pre-edit version.

EDIT:  well, if you see this then you are OK.  I suppose I should preview more and edit less!  ;-)

---

### Post by Connollyir on 2006-01-04
Well I didn't really feel like messing around with it too much so I just dealt with the big draw when I was copying stuff - which I finished a day ago so its trivial now. I did try and use alias cdcp='nice -n 10 cp' but it didn't work and I really didn't want to make a script that could (at least in my mind) potentially break stuff when I won't be using that operation too often (copying large files). 

I haven't gotten my system to exactly where I want it to be yet so you will hear back from me if the problem becomes more disruptive of my daily use, if it effects dvd buring/ripping for example.

Thanks for the help though.

-Ian

---

