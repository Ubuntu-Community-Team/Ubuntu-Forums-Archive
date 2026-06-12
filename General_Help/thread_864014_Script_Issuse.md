---
title: "Script Issuse"
date: 2008-07-19
forum: General Help
---

### Post by thestig_992 on 2008-07-19
Im kind of new to writing shell scripts, and im trying to write a script that will open transmission at midnight and close it at midday (because of my peak and off peak ISP stuff). I have most of it figured out, but it would be much easier if I could create a universal variable that would return 1 when transmission is already running and 0 if its not...

So my question is: how do i get a script to create a universal variable...OR...is there another way to find out if a program is already running...?

---

### Post by iaculallad on 2008-07-19
> **thestig_992 said:**
> OR...is there another way to find out if a program is already running...?

Use the terminal **top** command to view running all processes:

```
top
```

---

### Post by llebegue on 2008-07-19
Well actually transmission writes a file called

```
/home/<<user home directory>>/.transmission/gtk/lock
```

when the gui is running.

perhaps youu can use this information in a script :

```

if [ ! -e /home/<<user home directory>>/.transmission/gtk/lock ]
   then
   transmission &
fi

```

or something of that taste ...

---

### Post by llebegue on 2008-07-19
oh and if you want to turn it off just schedule a cron job with

```

killall transmission

```

---

### Post by thestig_992 on 2008-07-19
wow, thanks for all that, i should be able to get it going now...XD

---

### Post by Yannick Le Saint kyncani on 2008-07-19
> **thestig_992 said:**
> is there another way to find out if a program is already running...?

That would be something like this :

```

p=`pidof transmission`
if test $? -eq 0; then
    echo "transmission is running, its pid is $pid."
else
    echo "transmission is not running."
fi

```

---

### Post by thestig_992 on 2008-07-19
thanks again, thats working now

but I have another issue to do with manipulating strings...
I can use transmission to give me info about a certain torrent, as a string with lots of details...but i need to only extract the first part of that and save it as a new variable. The part of the string that i need ends when there is a space..

---

### Post by llebegue on 2008-07-19
Can give us an exemple of the whole string ?

---

### Post by thestig_992 on 2008-07-19
sure, if i type:
```
~$ transmission-remote -il
```
then it returns
```

ubuntu-8.04.1-desktop-i386.iso (694 MiB) - 0.00% downloading at 0.00 B/s (UL at 0.00 B/s), stalled

```

i planned on saving that as a variable, then changing it so that it was just the first part (ubuntu-8.04.1-desktop-i386.iso) which should be everyhting before the space.

---

### Post by llebegue on 2008-07-19
in a bash script you could use a variable such as :

```

myvar=$(transmission-remote -il | awk '{print $1}')
#do something here with ${myvar}

```

I don't now much about transmission-remote but if it gives you a list of file you might want to recurse through them before using the varaible 

```

for mytransmissionresult in $(transmission-remote -il)
  do
   myvar=$(echo ${mytransmissionresult} |  awk '{print $1}')
   #do something here with ${myvar}
  done

```

I haven't tested it but you may have to change some things if the file names contain spaces as a result of "transmission-remote" command.

---

