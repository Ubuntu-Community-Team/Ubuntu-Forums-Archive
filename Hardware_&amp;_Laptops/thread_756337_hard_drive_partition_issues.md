---
title: "hard drive partition issues"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by st.jordan on 2008-04-15
Hey all,

i was attempting to get the partition setup on my hard drive, when i realized that it had the primary partition as all of the 149gb's. right now im running windows xp and microsoft shockinglyis not being any sort of help.

thanks 
saint jordan
ps- im no noob when it comes to computers so dont be afraid to use technical terms

---

### Post by sam_delta on 2008-04-15
> **st.jordan said:**
> Hey all,

i was attempting to get the partition setup on my hard drive, when i realized that it had the primary partition as all of the 149gb's. right now im running windows xp and microsoft shockinglyis not being any sort of help.

thanks 
saint jordan
ps- im no noob when it comes to computers so dont be afraid to use technical terms

boot into a ubuntu live CD and run a program called GParted, you can resize/move current partition and make new ones with that program

you can run GParted in the live cd by typing in the terminal "sudo Gparted" or control-f2 and typing "sudo Gparted" as the command

sam_d

---

### Post by tenroc2o0o on 2008-04-15
Can you explain what you're trying to do and what happened a little better?

---

### Post by st.jordan on 2008-04-15
hey sorry i was in a bit of a hurry and wasn't articulating my thoughts well tenroc

the problem is that my c drive's primary partition is formated to use the entirety of the available space 
this presents a problem because i am attempting to setup a partition for linux to run on 
ps- any tips for size? my friend said 5gb should be sufficent.

---

### Post by sam_delta on 2008-04-15
> **st.jordan said:**
> hey sorry i was in a bit of a hurry and wasn't articulating my thoughts well tenroc

the problem is that my c drive's primary partition is formated to use the entirety of the available space 
this presents a problem because i am attempting to setup a partition for linux to run on 
ps- any tips for size? my friend said 5gb should be sufficent.

i'd recommend at least 10 G. , remember you can allways resize current partitions as mentioned in my previous post, so if ull like to make it bigger/smaller later, ull be able to do it.

Sam

---

### Post by st.jordan on 2008-04-15
one question about the live cd while i have u i downloaded the os i had just burnt the entire download to the cd and when i tryed to boot from it it would not run. is there only certain files that need to be placed on the disk? i presumed it would be a disk image but i didnt find one in the zip package.
thanks for your help
jordan

---

### Post by sam_delta on 2008-04-15
> **st.jordan said:**
> one question about the live cd while i have u i downloaded the os i had just burnt the entire download to the cd and when i tryed to boot from it it would not run. is there only certain files that need to be placed on the disk? i presumed it would be a disk image but i didnt find one in the zip package.
thanks for your help
jordan

you just need to burn the CD image you downloded,. search for an option in your favorite burner to burn ISO or burn CD image, you select the file path and you are done, nothing else to do

mayb u have to change the boot order of your computer in order to make it boot the CD, you can do this by entering your computer BIOS,  this is usually made by typing a key or comand while booting, this could be f12, for example.

while in the bios, make sure that in the boot order, the CD appears first or at least before the harddrive

Sam

---

### Post by st.jordan on 2008-04-15
thing is im not seeing any .iso files theres one wubi-cdboot.exe
i know there should be a disc image in the download because i did my homework on this beforehand and every thing ive read said burn the disc image to a cd or dvd
theres also a large folder titled isolinux  would this be it?

---

### Post by sam_delta on 2008-04-16
humm, as far as i know, u get a single .iso file, nothing more i just downloaded ubuntu hardy beta and thats what i got,

i dont know if what you have are the actual files of the CD or the iso content, 

did you downloaded it directly from ubuntu, you could try getting it directly from here

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by st.jordan on 2008-04-16
thats really weird im @ school right now but i downloaded gutsy from that exact page maybe i should try hardy when i get home :biggrin:

---

