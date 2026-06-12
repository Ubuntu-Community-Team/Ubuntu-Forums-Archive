---
title: "Processor Temperature Problem"
date: 2010-09-23
forum: Hardware
---

### Post by hagrid_aragog on 2010-09-23
I have a Intel Celeron D 2.53 Ghz, 1024+128 MB RAM, a 80 GB SATA+40 GB IDE+40 GB IDE

I am using xfce , and through the temperature sensors, i came to know that my processor reaches very high valus when the CPU usage is full.

My temperature observations have been as follows:(in degree celsius)
Idle: 56-57
Temperature as i am typing(with only google chrome and transmission on): 60
Light Process(Only songs):63-65
When medium Process is on( Eg: Movie on VLC): 69-70
When high Process: 78-80
The temperature has sometimes even reached the temperature of 82, and btw google chrome and transmission were on during the entire test.

Is this normal?????...The moment i close the process, the temperature immediately come down, hence i don't think this is a problem of heatsink cooling or thermal paste...Please help

---

### Post by PresenceofMind on 2010-09-24
> Is this normal?????

Sounds like your processor is running too hot for comfort. To give you an idea let me show you how hot mine runs.
 
AMD Phenom II X2 555 Black Edition (unlocked to X4) runs at:

Clock speed: 3.2GHz

Idle: 35C
Normal Use: 39C-42C
Heavy Use: 50C

Mind you I've unlocked mine into a quad-core and I'm not using the stock cooler. I would have expected Celeron dual cores to run a lot less hot.

Usually, processors have an upper limit of around 70C and 82C will certainly reduce it's life in the long run. How long have you had your machine for?

---

### Post by hagrid_aragog on 2010-09-24
What????!!!!......That is my approximate cabinet temperature( 30 degree celsius)......i have no clue what's going on.......i have been using this PC for 4 and a half years

btw my PC shutdown temperature is 85 degree celsius....

---

### Post by endotherm on 2010-09-24
celerons of that era ran hot. try getting a new heatsink, and be very careful to use the correct about of thermal grease when installing it. make sure your other fans are working correctly, and if all else fails, try putting it in a larger case. you are right, the cooling is working as is, so your temps drop quickly, but the sink/fan isn't doing anything to keep it from reaching that temp in the first  place, so perhaps something with some bigger guns is required.

also as a stopgap, you may want to add the frequency/CPU scaling applet to your panel, and set it to on-demand. it will run your CPU at 800MHZ when not in serious use, so you will get less heat off it.

---

### Post by hagrid_aragog on 2010-09-24
I am no computer engineer.....i applied the amount of paste that i felt correct, could that possibly be a problem....a slightly grater amount that is??????...........

---

### Post by PresenceofMind on 2010-09-24
Normally, you only need to apply a very thin layer of thermal compound. The paste is only meant to fill small, microscopic cracks on the surface of the CPU package and allow heat to escape better.

Applying too much may cause the heat to escape slower than normal and will cause overheating. Conductive thermal pastes (such as Arctic Silver) can also short circuit the mobo if it is everywhere.

You only need to apply a bit (the size of a grain of rice) and spread it across the surface until it covers it entirely. If it looks excessive then clean of a bit using tissue paper.

---

### Post by hagrid_aragog on 2010-09-26
Phew!!!!....Problem solved.........mow my idle temperature is around 48-50 and maximum temperature around 60-62.....What i did is........I removed and reapplied  an unsettlingly low amount of thermal paste........and that seems to have done the magic......:)


Thank you all....thank you for your helpful inputs......

---

