---
title: "Not ubuntu specific but just seekin general guidance"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by mattgaunt on 2007-01-29
Hey everyone

Im just posting this because last 2 days my computer has started acting very strangely and just need some advice, this is basically what my computer is doin

Basically sometimes it will turn on fans and everything turn on but nothing comes up on the screen just the HDD light stays on. Other times it will boot up and seem fine but eventually just cut the power and turn off, most of the time if it cuts out when I turn it on, it will not bring anything up on the screen and the HDD light stays on.

And sometimes my computer will be fine

Now this is when i boot in both windows and linux, so just wondered if anyone had any ideas??

Thanks alot

Matt

---

### Post by kairu0 on 2007-01-29
Fans turning on and the computer suddenly turning off sounds like you have an overheating problem. When the CPU temp crosses a threshold sometimes the BIOS kills the power. It could also be that your power supply is delivering an inconsistent level of power, and might need to be replaced.

If you have a temperature monitor in your BIOS, watch it for a while to see if things get too hot. If you can use libsensors in Linux or Speedfan (free to download) in Windows, you could also check.

---

### Post by kevinlyfellow on 2007-01-29
my folks experienced that phenomenon with their emachines... it became worse as time went on and eventually bought a new emachines (I don't know why they did that after having their box die an unusual and untimely death).  

Anyways, check to make sure that its not overheating
```

cat /proc/acpi/thermal_zone/THRM/temperature

```

check to see if its not the power supply failing (i don't know how to do that exactly)

last guess I have is that your running emachines

---

### Post by logos34 on 2007-01-29
Your power supply is probably dying--specifcally, undervoltages rather than overheating although that's possible too...Do like kairu suggests and dl Speedfan (windows)...I had a psu go out just a few months ago and had pretty much same symptoms...starts up and everything seems like its working but then os won't load, blank screen...

---

### Post by mattgaunt on 2007-01-29
Cheers for the help guys, to be honest i have a kick *** machine but a crappy PSU, cheep and cheerful but ive already has a processor burn out on me and to be honest i was scared that would be the cause of it, although the processor was under warranty still.

Ill check for overheating, but im hoping it is the power supply, i was also suggested by a friend that it could be the DVD drive playing up but not sure how the would affect the boot problems.

Its just weird how sometimes its fine
But ill keep u all post and thanks again

Matt

---

### Post by mattgaunt on 2007-01-29
The core temperature which im guessing is the CPU temp is staying arnd 46C so that isnt too bad is it??

I mean i dont think these CPU's are the best but i dont think this is the problem, i am thinkin it is the power suplly since i put this machine together and i did get a fairly cheap and cheerful power supply

So does the CPU temp help at all? 

Thanks for the help again

Matt

---

### Post by mattgaunt on 2007-01-29
[IMG]http://i26.photobucket.com/albums/c112/mattgaunt/CPUandPowerSupply.jpg[/IMG]

---

### Post by mattgaunt on 2007-01-29
I dont know if that helps but the voltages on the right hand side dont look too great, i mean i could be completely wrong but it anyone could give me any idea what they think is the problem that would be great

Matt

---

### Post by Daveth on 2007-01-30
might be worth you digging out an old copy of CustomPC magazine from last year- they did a review of power supply units. Importantly the cheapie ones were not only inefficient in their power conversion but also failed to deliver the load they promised on the side of the box. One even burst into flames! Though they cost a lot I have a Seasonic 600W in my new box - some 84% efficient and high stability on the power rails. And, of course, if you move PC you can always take it with you.

David

---

### Post by mattgaunt on 2007-01-30
Cheers david, yeah i went an ordered myself a new Akasa power supply which had gd reviews and was a bit expensive but i am hopin ill get what i pay for.

Thanks for the advice ill let you all kno how it goes when i fit it in, for now ill just have to make do with the random power cuts on my computer lol

Thanks again everyone

Matt

---

### Post by mattgaunt on 2007-01-31
I got the PSU today and fitted it and everythin seems to be 100% ok!! so im so incredibly happy it wasn't something wrong with m/b or CPU

But thanks you so much everyon for helpin me out, plus this whole experience means i have a much much better PSU, its still only 400W but it is such a higher quality

Thanks again

Matt

---

