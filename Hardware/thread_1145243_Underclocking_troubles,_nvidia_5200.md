---
title: "Underclocking troubles, nvidia 5200"
date: 2009-05-01
forum: Hardware
---

### Post by Barlam on 2009-05-01
I used to have Ubuntu 8.04 on my old Toshiba laptop with the 5200 nvidia graphics card. The laptop is a bit old so had to be underclocked to prevent overheating. I used nvclock, though I'm not sure which version. Now I upgraded to Xubuntu 9.04 and tried to install nvclock via command line. It installed but whenever I tried to use it I got the error "***Stack smashing detected***". I downloaded an older version and compiled it myself, however whenever I tried to use it it said: "mobile gpu's not supported", I tried the -f option to no avail. Is there someway I can get the laptop underclocked without going back to 8.04? The laptop is unusable at the moment.

Cheers, Tom

---

### Post by WSmart on 2009-07-31
I got that with 9.04 on my desktop. the stack smash error with NVClock 

Can you set voltage on the GPU in your BIOS?  That would help.  Or drop the speed or volate on the CPU.  Fans on laptops will commonly fail.  It might only need a drop of oil.  Lots of dust and lots of heat means lots of fan problems.

Thanks all!:popcorn:

---

### Post by Barlam on 2009-08-06
It's fairly difficult to use the bios because the graphics are so knackered that characters do not display correctly when in the bios You can guess the simple stuff but anything complicated is fairly hard.

---

### Post by Barlam on 2009-08-06
Just had a look in the bios, there is only CPU under-clocking available. Graphics are what need doing most

---

