---
title: "Vaio VGN-FZ18M"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by harryBoy on 2007-09-25
hi can anyone tell me if i am able to install ubutno in my laptop its a sony 
Vaio VGN-FZ18M i tired once but i get an errore message i was wondering if thiere is dirver as i am not even able to install xp pro i contacted sony and asked them for xp driver and i got to konw that only for vista the drivers are available tat is it 

can anyone tell me if i can install any of linux software for my laptop 
thanks in advance

---

### Post by kerry_s on 2007-09-25
what was the error?

---

### Post by harryBoy on 2007-09-25
it was something with bash root etc when it was booting from the cd i will try to nite at home and will write down the complete message here 
if i want to keep vista shall i install vista first or ubuntu? 

and how much shall i chose my swap partation i have 2gb ram someone told me that is hould be double of the ram is tat rite?

thanks for answer

---

### Post by 444 on 2007-09-25
Install Windows before Ubuntu.

You don't need a lot of swap, only 1gb should be good.

---

### Post by kerry_s on 2007-09-25
bash error make sure you check the cd, might be bad burn. it should be burned as a image at 4x for best.

1gig swap is enough, you probably will never use swap with 2gig, but it's good just in case some app go's crazy and starts eating up memory the system shouldn't freeze. you might want to make it bigger if your going to use suspend or hibernate, if that even works. vaio's are a bit of a pain cause sony only wants you to run what they give you.

---

### Post by tvrg on 2007-09-25
I have a vaio VGN-FZ11S and i needed to install using the alternate cd, the error i got whas the tty job control stuff you see posted everywhere

---

### Post by harryBoy on 2007-09-30
i have vista installed and now when boot ubututu it gives me the following errore


busybox v1.1.3 ( debian 1:.1.1.3 -3-3ubutntu) built in shell (ash)
enter help for list of built-in commandes
/bish/sh: can not access tty; job control turned off(initrafms)

can anyone help me with it 
thanks

---

### Post by harryBoy on 2007-09-30
i even burnt the cd with a 4x speed  with infrarecord but still same problem

---

### Post by tvrg on 2007-09-30
as i said, use the alternate cd, on the download page make sure you tick "alternate cd"

---

### Post by harryBoy on 2007-09-30
> **tvrg said:**
> as i said, use the alternate cd, on the download page make sure you tick "alternate cd"

ok i will try this and write down the result

thanks

---

### Post by harryBoy on 2007-09-30
i did the installation and whn i boot the pc it gives me the following boot option

vista boot
ubutntu kernel generic 
and ubutngu kernel generic recovery

when i click on the first one as linux is my default os boot

aftr loading the ubuntu boot image 
itsays

the server X startup (graphic interface failed)

it can be that it wasnt configuer correclty

do you want to read the messages

after cliking yes


it gives m info about the linux os 

a long message at the end it says 
nv(0) no display devices found

screen foun but non have a usable configuration 
fatal server error no screens found

anyone know what the problem is ?

---

### Post by David A Knight on 2007-09-30
To get the live cd to work on my FZ11M I added 

all_generic_ide nosplash

to the command line to boot with and it worked without needing to resort to the alternative cd.  I also need those options to boot the actual installed version, or did a couple of months ago, not tried without.

---

### Post by harryBoy on 2007-09-30
> **David A Knight said:**
> To get the live cd to work on my FZ11M I added 

all_generic_ide nosplash

to the command line to boot with and it worked without needing to resort to the alternative cd.  I also need those options to boot the actual installed version, or did a couple of months ago, not tried without.

i didnt understand what u said 
did the live cd work with 
the alternate cd installation finished but i cant acces to graphic interface

---

### Post by ZipoTe on 2007-10-01
let's do some work :)

ok, after the X server error appear, you will get into a terminal, then type this:

```
sudo nano /etc/X11/xorg.conf
```

Look for Section "Device", here you will find something like:

```
Driver         "nv"
```

just replace "nv" for "vesa"

save changes and reboot.

---

### Post by tvrg on 2007-10-02
the GeForce Go 8400M GT needs the latest nvidia driver, use envy or download it

---

