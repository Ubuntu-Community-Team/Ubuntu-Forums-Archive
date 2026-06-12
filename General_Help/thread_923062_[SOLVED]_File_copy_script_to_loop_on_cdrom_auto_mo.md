---
title: "[SOLVED] File copy script to loop on cdrom auto mount"
date: 2008-09-18
forum: General Help
---

### Post by covert on 2008-09-18
I have a bunch of CD's I want to copy to the HD.

I made a simple script

```
#!/bin/sh
cp /media/cdrom/* /media/terradrive/.
eject

```

Now what I want to do is make the script so it waits for the tray to close and the cdrom to auto mount then start the next copy cycle..

so

cp /media/cdrom/* /media/terradrive/.
eject
wait for auto mount after try goes back in..
cp /media/cdrom/* /media/terradrive/.
eject
wait for auto mount after try goes back in..

and so it.

Is there a wait command I can use or a triggered event for when the cdrom auto mounts I can include in my script ?

---

### Post by Mister.Vash on 2008-09-18
You can start off with the sleep command
sleep 5
will wait 5 seconds

I'd start off with just the sleep and see if it works for you.  You can always focus in on adding triggers or checks later if needed

---

### Post by leef on 2008-09-18
I haven't tested this (as I don't have a use for it) but something like this should work;

```

CDDEV="<CDROM DEVICE>" #sdb for example

COUNTER=1 # setup an everlasting loop
while [  $COUNTER -eq 1 ]; do
  input=$(mount | grep $CDDEV | gawk -F/ '{ print $2 }'); # check to see if device is mounted.
  if [ $input -eq dev ]
  then
    cp /media/cdrom/* /media/terradrive/.
    eject
  fi
done

```

CTRL + C should exit the loop, if you get any error let me know :-D .

---

### Post by covert on 2008-09-18
I considered using the sleep command. It will not work since the time it takes to change a CD could be a few seconds if I am next to it to a few minutes when I notice the draw is open waiting for the next disk.

Thanks for the idea.

---

### Post by covert on 2008-09-18
Thanks leef. I will give it a shot. Looks promising :)

---

### Post by covert on 2008-09-18
Thanks for the help. This is the final script. Works a treat.

```
#!/bin/sh

CDDEV="/dev/hda" #sdb for example

COUNTER=1 # setup an everlasting loop
while [ $COUNTER -eq 1 ]
do
  input=`mount | grep $CDDEV`
   if [ -n "$input" ]
   then
    cp /media/cdrom/* /media/terradrive/.
    eject
  fi
  sleep 1
done
```

---

