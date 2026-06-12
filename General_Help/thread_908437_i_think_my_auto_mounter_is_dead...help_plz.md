---
title: "i think my auto mounter is dead...help plz?"
date: 2008-09-02
forum: General Help
---

### Post by Meow27 on 2008-09-02
so ive kinda been screwing around with my laptop lately and then all of the sudden (i have been touching some stuff but i dont remember how i did it)

whenever i plug in my flash drives, try to connect to other locations (other than the web), nautilus gives me the error message ¨Nautilus cannot handle computer: locations.¨

(i have to manually mounmt everything which is tedious and all the files in the dirves are treated as root so i cant do much there)

my laptop is basically isolated now and im not necessarily looking for a complete fix. all what i really need is a good way to get 3 gb of my files into my desktop (no i will not do it thru aim or anything like that)

i recently tried transferring with samba but i cant for the strange reason written above.

would it work if i took this HDD and used it as an external on my linux desktop?

---

### Post by oobe-feisty on 2008-09-02
check if hald is running "ps aux | grep hald"

if its not sudo /etc/init.d/hal restart

---

### Post by Meow27 on 2008-09-02
restarted it, nothing has improved (this is a 2 week old problem if that helps :P) :(

---

### Post by oobe-feisty on 2008-09-04
well if you cant fix auto mounting but all you want to do is mount an external drive to copy files then you can mount the driver manually 

e.g mount /dev/sdax /mnt/tmp 

this should work replace x with the actually number 

if you dont know type 

ls /dev/sd* 

before you attach the device then 

ls /dev/sd* 

after 

you should see a new /dev/sdb1 or somthing

---

### Post by Meow27 on 2008-09-05
ok ill try that when i get something to put the HDD into.

thanks

---

### Post by epictetus on 2008-09-08
Could you post your problem at the Launchpad thread for the "Nautilus cannot handle" bug?  [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889)

It seems a number of people are having this issue, but its importance is ranked as low.

---

### Post by Meow27 on 2008-09-08
ok the guide isnt working for me

can you [or someone else] give me a step by step guide for mounting my drive please? this is all extremely confusing for me :(

(the wahts now an external drive is formatted in RieserFS is that helps)

edit: nvm i got it to auto mount... apparently i didnt stick it in the slot completely ;/

---

