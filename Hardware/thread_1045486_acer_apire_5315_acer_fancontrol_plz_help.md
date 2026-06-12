---
title: "acer apire 5315 acer_fancontrol plz help"
date: 2009-01-20
forum: Hardware
---

### Post by majingohan99 on 2009-01-20
hey my laptops fan ain't workin but i know wot to do, but im to attuned to windows to understand it so cud u plz explain it me like im a complete idiot:

[http://ubuntuforums.org/showpost.php...&postcount=117](http://ubuntuforums.org/showpost.php...&postcount=117)

thnxs

BTW

i've got so far put it still dusent work i changed it to my settings tested it but fan is still not workin

it even went up to "3rd gear"

terminal :

majingohan99@majingohan99-laptop:~$ tar xvfz /home/majingohan99/Desktop/acer_fancontrol.tar.gz
acer_fancontrol/
acer_fancontrol/acer_fancontrol
acer_fancontrol/mempat
majingohan99@majingohan99-laptop:~$ gedit acer_fancontrol/acer_fancontrol
majingohan99@majingohan99-laptop:~$ sudo ./acer_fancontrol/acer_fancontrol
[sudo] password for majingohan99:
./acer_fancontrol/acer_fancontrol: 210: mempat: not found
Clutch down
./acer_fancontrol/acer_fancontrol: 210: mempat: not found
2nd gear
./acer_fancontrol/acer_fancontrol: 210: mempat: not found
2nd gear
./acer_fancontrol/acer_fancontrol: 210: mempat: not found
3rd gear

---

### Post by JoeFriday49 on 2009-12-25
Did you ever find a resolution to this problem?...  I have the same thing going on now...

---

### Post by slumbergod on 2009-12-27
I think I have solved it. The script calls the mempat as a command and it looks for it in the /usr/bin/ directory which it isn't yet in unless you move it there.

You have two options:
1. modify the script so that wherever you see the mempat command you append the path to it at the front; or more easily:
2. just copy it to the /usr/bin/ folder:
sudo cp mempat /usr/bin/

---

### Post by JoeFriday49 on 2009-12-28
> **slumbergod said:**
> I think I have solved it. The script calls the mempat as a command and it looks for it in the /usr/bin/ directory which it isn't yet in unless you move it there.

You have two options:
1. modify the script so that wherever you see the mempat command you append the path to it at the front; or more easily:
2. just copy it to the /usr/bin/ folder:
sudo cp mempat /usr/bin/

That may be this fellows problem, but I get the following error when running the same script:

mmap() failed: Operation not permitted
Failed to map length 2 at address 3f6bceaf error 1
Clutch down

My mempat file is in the correct directory, but the script still won't work.  Here is the thread I've posted my details in:
[http://ubuntuforums.org/showthread.php?t=1362557&highlight=acer_fancontrol](http://ubuntuforums.org/showthread.php?t=1362557&highlight=acer_fancontrol)

---

### Post by slumbergod on 2010-03-25
The best solution of all, even better than the patch, is to buy a laptop cooling pad like the belkin or targus one. Using this my laptop temp is 45 when I do nothing, 55 watching an xvid. Even those annoying HD ones that stress my laptop to the point of shutting down seem to stay under 85.

---

