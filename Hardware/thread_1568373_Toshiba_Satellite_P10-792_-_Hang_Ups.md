---
title: "Toshiba Satellite P10-792 - Hang Ups"
date: 2010-09-05
forum: Hardware
---

### Post by Allenseph on 2010-09-05
Hello,

It's a while that I've been trying to install Ubuntu 10.04 on this particular laptop. Already at installation it would hang up randomly, but eventually I managed (after 5 tries or so).

Then everything would work normally, even suspend and the thermal fan, but after a while the laptop just hangs up, totally randomly, but only when actually *using *the computer.

This also happens with the new version, 10.04.1. I don't have this in Windows XP Professional. 

Technical information about this laptop can be found here: [http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&DISC_MODEL=0&ACTION=PRINT_WITH_BACK&com.broadvision.session.new=Yes&PRODUCT_ID=85872](http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&DISC_MODEL=0&ACTION=PRINT_WITH_BACK&com.broadvision.session.new=Yes&PRODUCT_ID=85872)

The BIOS is updated to 1.60.


Thanks,

Allenseph

---

### Post by Allenseph on 2010-09-07
At least you could tell me *why* you won't/can't help me.

Yes, I've searched the forums and other sources for solutions, and have found nothing that was a real help to me (else I wouldn't post, right?)

Maybe didn't I tell that I'm an "absolute beginner", but I thought that would be concluded from my comparisons with Windows XP.

Maybe you need some more information about how I installed Ubuntu, well here you have it:

First, I didn't do anything fancy during the installations, I just took the standard/recommended options. I chose that Ubuntu had the whole hard-drive available for itself.

For 10.04, I used a magazine DVD; the first 4 times or so, the installation crashed, like said, at random moments. After that I gave up and restored Windows from the Toshiba-DVD. A while after that I tried again and for some reason (perhaps coincidence) it did install then.

Great, I thought, until I encountered the crashes described in post #1

With 10.04.1 coming out, I decided to give it another go. First install (burned cd), crash. Second install (unetbootin) crash. Third install (also unetbootin), success. After that I find out that nothing seems to have changed however; the same crashes appear again and again.


Some other things:

Once the laptop crashed during hard-drive activity; the hdd-light kept burning (steadily)! Shows the severity of those crashes I guess.

Further, as you know, the package "toshset" is shipped with Ubuntu 10.04; when I use it, it says "required kernel toshiba support not enabled". Could this be the cause of my problems?

Also is there this other thing that doesn't work: "hibernate" or suspend-to-drive. When recovering from this state, I only get a black screen with the mouse pointer on it.


If there's anything else you need, please, just say it.

PS: My laptop isn't connected to the Internet.

---

### Post by AlexZaim on 2010-09-07
Hey, ppl usualy don't respond because they don't know what to say. But you can always bump three times a thread.

If it hangs during a long I/O operation then it is a kernel bug. It will be fixed in 2.6.36... or 2.6.37 in worst-case scenario.
Either than this i don't know with what to help. sorry

---

### Post by Allenseph on 2010-09-09
Hello AlexZaim,

thank you for replying.

> **AlexZaim said:**
>  It will be fixed in** 2.6.36... or 2.6.37** in worst-case scenario.


My kernel was 2.6.32, so I hadn't tried out 2.6.35, which is shipped with Ubuntu 10.10 Maverick Meerkat (Bet), yet.


I downloaded the image, burned it on a CD (unetbootin wouldn't work), and installed with standard options (over 10.04.1, single boot). The installation completed at the first attempt. Maybe a coincidence, but I hoped not.

After clicking the "restart" button, my screen got eventually filled with messages saying "I/O Error". So I had to reset the computer. Booting after that went normal however.

Shortly afterwards, I ran "sudo lshw" in the terminal. Crash. I tried several times to reproduce this, and strangely, every time the computer would crash at "SCSI". I did not have this in 10.04.1.

Also did the random crashes not disappear. The rest, like in 10.04.1, works fine (except for hibernate, again).


What intrigues me though is that this particular laptop would work, with kernel 2.6.14. [http://www.kroon.co.za/howto.php?howto=toshiba_p10](http://www.kroon.co.za/howto.php?howto=toshiba_p10)

Kind Regards,

---

### Post by lakyman on 2011-01-06
ciao a tutti io installo ubuntu su parecchi pc e diverse versioni ma su thosiba satellite p10792 non ci sono riuscito.ho provato almeno 10 volte e differenti versioni ma il risultato e' il blocco totale ,non si spegeva nemmeno.per questo capisco che l'amico in questione trovi difficolta' nell'installare ubuntu su questo pc.se qualcuno sa qualcosa in piu' si faccia vivo ,da parte mia ho rinunciato .LE STRANEZZE DEI PORTATILI THOSIBA.

---

