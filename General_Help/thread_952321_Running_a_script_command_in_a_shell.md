---
title: "Running a script command in a shell"
date: 2008-10-19
forum: General Help
---

### Post by TroyDowling on 2008-10-19
Hey,

So, I'm a massive fan of Nautilus Scripts and I use them for just about everything I do on a day-to-day basis. Recently I wrote five scripts for running a 'ClamScan' on different parts of my system. This is one of them for scanning my storage drive.

```

#! /bin/bash

if [ -d /media/Storage ]
then
	cd /home/troy/Desktop
	gnome-terminal -e --title="Virus Scan" "clamscan -ri --log=VirusScan_Storage.txt /media/Storage"
	zenity --info --text="Finished scan."
else
	zenity --info --text="The Storage drive was not found!"
fi

```

It works and does exactly what I tailored it to do aside from one thing. It does execute the scan in a pop-up terminal, and all the results are displayed in this terminal, but then once the scan completes, the terminal disappears! It finishes it's command and pops away... I'm looking for a way to make the terminal pause, preferably with the 'read' command. I tried this...

```

...
gnome-terminal -e --title="Virus Scan" "clamscan -ri --log=VirusScan_Storage.txt /media/Storage && read"
...

```

but then ClamAV interpreted the && and 'read' as things it was supposed to scan! If I put the read outside the 'gnome-termina' command, the terminal still closes and my script pauses... Can anyone help me? I did write it out so that instead of using terminals at all, I just used 'zenity' to print out the log file in a text blurb. I'd really prefer to have it all in a terminal though and I'd love to know the solution to this problem for the future.

Thanks,
Troy.

---

### Post by CharonM72 on 2008-10-19
EDIT: Nevermind, not applicable.

---

### Post by TroyDowling on 2008-10-19
Ha, yeah, but I'm looking to use these as Nautilus Scripts. Thanks anyways.

---

### Post by bodhi.zazen on 2008-10-19
Write you script 

```
#!/bin/bash
command1
command2
read
command3

exit0
```Instead of using gnome-terminal -c in the script however, call the script with gnome-terminal

ie rather then 

gnome-terminal -e command1

just use "command1" in a script

Now call the script with

gnome-terminal -e /path/to/script

---

### Post by TroyDowling on 2008-10-19
Yeah, I should have mentioned this in my original post. I did do that as well. I made two scripts, one referencing the other like so. It worked, but it wasn't the cleanest solution. I'd really love for this to be just one file. I suppose I could do classes and that. That's just side stepping the issue though. I guess if I'm going to spend this much time on it anyways, I'll just rewrite it in Ruby or Python. :P

---

### Post by bodhi.zazen on 2008-10-19
Just make a launcher rather then a nautilus script. You can add the launcher to your menu or your panel.

Or if you *must* have the script call itself in a gnome-terminal;

(just a suggestion, you may need some minor modification, like say a while loop rather then an it then).

#!/bin/bash

x=0

if x =0 ; then
gnome-terminal -e "$0 $@"
x=1
exit 0
else
exit0
fi

---

### Post by TroyDowling on 2008-10-19
That looks like an infinite blackhole waiting to happen... I do want to have the Nautilus Script because I have around fifty or so scripts all nicely organized and ready and the click of a button. I suppose I'll just take the penelty of clutter and go back to my two-script setup. Luckily I have another script for sync'ing all my scripts between my Desktop and Laptop. :)

If I get around to it sometime, I'll write that improved script in Ruby or Python and post it here if anyone is interested. I'm definitely no guru, but I'm savvy enough with Ruby to get the job done.

---

### Post by bodhi.zazen on 2008-10-19
Yea, it is definitely a rough draft , probably a while loop is best.

---

### Post by TroyDowling on 2008-10-19
Haha, yeah. I'm just too tired to tackle this tonight. It's late, well early, where I am and I'm just finishing up what I'm doing here before I head out to bed. Thanks for the help on this, I'll probably bump the thread sometime on Monday when I have the time to rewrite those scripts.

Thanks again.

---

