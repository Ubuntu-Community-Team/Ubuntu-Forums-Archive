---
title: "Status of Nvidia geforce 420M (and other optimus) cards?"
date: 2011-05-20
forum: Hardware
---

### Post by Naggobot on 2011-05-20
What is the status of newer Nvidia (Optimus) cards with Linux. 

Proprietary driver states that it supports

GeForce GTS 450
  GeForce GTX 460M
  GeForce GT 415M
  GeForce GT 425M
  GeForce GT 420M
  GeForce GT 435M
  Quadro 2000
  Quadro 600 

cards but by Googling it is easy to find a lot of stuff stating that Nvidia will not support Optimus cards. 

I am asking since I consider buying a laptop with 420M card and I would hate to spend 300€ extra just to use internal integrated chipset. 

So do these actually work with Nvidia prorietary driver with 3D properly enabled?

Thanks

---

### Post by ajgreeny on 2011-05-20
Have a look at the final post #15 of [http://ubuntuforums.org/showthread.php?t=1586292](http://ubuntuforums.org/showthread.php?t=1586292) which has two links which may help.

---

### Post by Naggobot on 2011-05-20
Thank you

This does help especially decision making. 

I suspect I will spend 300€ less and not have Nvidia Card. I need to sleep over it though and read through the material with a sharp eye. I have to consider the fact that I want to keep on using lucid until the end. 

I have to admit that Martin Juhl has done pretty impressive work and it will hopefully lead to complete Linux support and wider adoption in near future. 

I just still keep on wondering what features the Nvidia proprietary driver offers? Does the proprietary driver run all of the applications through GPU or does it just turn off the GPU and keep on running in the embedded chip?

If it is the latter then it probably is the biggest ripoff for a some time.

---

### Post by Naggobot on 2011-05-20
I add just one more item to this thread

This is from the latest Nvidia 32bit driver read me

> ome designs incorporating supported GPUs may not be compatible with the  NVIDIA Linux driver: in particular, notebook and all-in-one desktop  designs with switchable (hybrid) or Optimus graphics will not work if  means to disable the integrated graphics in hardware are not available.  Hardware designs will vary from manufacturer to manufacturer, so please  consult with a system's manufacturer to determine whether that  particular system is compatible.

i.e. it depends on the manufacturer design if some particular hardware will work with Optimus chips. Alternative method may the "Bumblebee" by Martin Juhl. 

So when buying new hardware packed to laptop form factor it is difficult to know before hand.

---

### Post by dugh on 2011-05-21
I installed bumblebee but compiz and so forth still don't work due to other nvidia bugs.  And if you try the ubuntu-bugs command line tool that you are supposed to use to report bugs now, it won't accept your bug report.

---

### Post by kamrulahasan on 2011-05-30
im using asus N53JQ laptop. im new at ubuntu 10.04.02  i cant enable my Nvidia geforce gt 425M graphics card. if someone can help me then i will continue with ubuntu. otherwise i will be back to windows.

im finding the solution for three days and find nothing.

---

### Post by kacperpl1 on 2011-05-30
Check out if there's bios update for your notebook that will enable switching on and off integrated GPU(GMA 500) if your notebook's CPU has one.
Optimus support is still not there.

---

### Post by Naggobot on 2011-06-01
It seems that there is activity in this thread beyond the original scope. There fore I change the status to unsolved for a while. If the discussion stops for a longer period then I will change the thread back to solved.

---

### Post by Naggobot on 2011-06-10
Reverting the thread back to solved

---

