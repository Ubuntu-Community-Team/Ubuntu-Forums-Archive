---
title: "[SOLVED] installing pakages.. without network!!"
date: 2008-10-19
forum: General Help
---

### Post by ultrabyte on 2008-10-19
okay, im new to ubuntu
ive installed ubuntu (studio) on my computer and i am trying to get my rt73 wireless adator to work

but this isnt network question..

i found the guide to installing rt73 module manually. which is..
[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)
and so i downloaded the pakage for rt73,
the guide told me to expand the thing and go to module folder and do the commands: make
boom
it says
make : *** /lib/modules/2.6.24-19-rt/build: no such file or directory ...... rt73.lo failed to build! blah blah
and i directly went to the destination, as i expected, "build" folder was not there. (tried making that folder manually but it says i have no permission)

im GUESSING this is because my kernel(?) or language or make program or i dont know how to call it is not upgraded.. but to upgrade. ILL NEED A NETWORK!! 
oh my god how do i do this..

im in the same situation with other pakages like ndiswrapper
i try to do 
sudo apt-get install ndiswrapper-common
it tells me it couldnt find that pakage..

same with sypnatic pakage manager, to upgrade , ill need network, but lol i has no network...






i dont know why that "make" doesnt work!! help me please!
the simplest compiling method, doesnt work with me..



ps
does anyone know why i dont get any sound with "vurtual midi keyboard"? i dont know how to set the sounds..
and also, does anyone know how to make "shortcut" so when i drag a file or folder to that shortcut, i can run it in su?




THANK YOU

J

---

### Post by oldos2er on 2008-10-19
The ndiswrapper packages should be on the Ubuntu install CD. I think you'll need to also install build-essential.

---

### Post by ultrabyte on 2008-10-19
oh good
how do i doo that?!?!?!?!
and what do i do if there isnt those pakages in the CD?

thank you ann
j

---

### Post by oldos2er on 2008-10-19
Point your sources.list to the CD. In Gnome, go to menus System, Administration, Software Sources, check the box next to CD-ROM, and uncheck the boxes under 'Downloadable from the Internet'. Then Reload.

---

### Post by CloudFX on 2008-10-19
Another option would be to simply connect your computer directly threw an ethernet cable.

---

### Post by ultrabyte on 2008-10-19
i got the list of programs from CD
but there still werent the programs i need
there werent anything called build essential nor ndiswrapper
all i got were the language files which i didnt install...

i heard that they didnt include build essential in 8.04.. maybe thats why?
then how am i supposed to update...

can i download build essential from other places?
so i can put it in my usb and transfer to ubuntu

and no, i cant use the ethernet cable
router is downstairs and i cant be bothered to take me pc downstairs...



THANK YOU

J

---

### Post by oldos2er on 2008-10-19
You need to run "sudo aptitude update" after you add the CD as a repository, so that apt-get will "see" it.

---

### Post by ultrabyte on 2008-10-19
still doesnt apear..
they are not even in the list....
thank you ann

J

---

### Post by ultrabyte on 2008-10-19
I did tell you that its ubuntu studio right?
coz other people seem to have same problem with me

im pretty sure that there werent any other pakages rather than languages in the sypnatic package manager which isnt installed...

---

### Post by ultrabyte on 2008-10-19
okay i found out that in
pool/main/b/
of the studio CD, there wasnt build essential while normal ubuntu CD has them.

now i know build essential will solve all my problem
and i need to know how to install build essential without the CD nor network

---

### Post by oldos2er on 2008-10-19
> **ultrabyte said:**
> still doesnt apear..
they are not even in the list....
thank you ann

J

 Sorry for bad advice. I downloaded Ubuntu Studio myself just to see what was up, and it appears (as you noticed) that its CD does not include either ndiswrapper or build-essential. If you've got another machine with internet access, download the standard Ubuntu Live CD (from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)), burn it to a disc, and from there you'll find these two programs.

---

### Post by ultrabyte on 2008-10-19
you know what
thank you so much
you actually downloaded the studio to answer my question..

we need more of people like you around the world

---

### Post by oldos2er on 2008-10-19
I have a broadband connection so it's not that big of a deal. Anyway, I hope you can get your problem resolved.

---

