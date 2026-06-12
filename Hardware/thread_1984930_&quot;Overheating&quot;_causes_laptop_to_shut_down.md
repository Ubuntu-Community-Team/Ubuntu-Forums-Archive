---
title: "&quot;Overheating&quot; causes laptop to shut down"
date: 2012-05-22
forum: Hardware
---

### Post by goaliedude3919 on 2012-05-22
The reason "overheating" is in quotations is because I don't think the computer is actually overheating. I recently updated from 11.10 to 12.04. On 11.10, I had no problems with overheating, unless I was blocking the fan. Even then, the computer would get hot enough to practically burn you before it would shut down. 

However, ever since I upgraded to 12.04, my computer regularly shuts off when the computer is very cool to touch. When I boot it back up it tells me that the system was getting too hot. The specific error that is occurring is "thermal system board thermal trip". Also, most of the time the fan is running constantly on the highest setting (at least it sounds like the highest setting). 

As I'm using it right now, it seems to be doing much better and the fan isn't constantly blasting. Hopefully this is a sign that this bug has worked itself out, but just in case, I'm hoping someone can tell me what is going on.

I guess I should probably add that I have a Dell Latitude E6420. The processor is an Intel® Core™ i5-2520M CPU @ 2.50GHz × 4 . The graphics is a NVS 4200M/PCIe/SSE2.

---

### Post by gordintoronto on 2012-05-22
I use lm-sensors. [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

I also use Conky to monitor temperatures, among other things. Conky uses a conkyrc file to tell it what to do, and that depends on the details of your hardware. So my conkyrc file would be of little use to you, since I have a different CPU and video card.

You can also install hddtemp to see how hot your hard drive is.

---

### Post by goaliedude3919 on 2012-05-23
I've added the programs you suggested and through Psensor (hddtemp) it shows that my GPU is in the high 50's and low 60's while temp1 is at 25C and /dev/sdais at 36C. Could it be the GPU that is overheating?

Also, I have noticed that the overheating problem only occurs when my laptop is plugged in to charge. I can use it all I want unplugged and I have no problems, but it starts to get hotter when plugged in. This has never happened before. Is there a way to fix that?

---

### Post by 2F4U on 2012-05-23
From the temperatures you post it looks as if the graphics card would be the problem. Which graphics driver are you using? The open source drivers are not as good in power management as the proprietary ones.

---

### Post by roelforg on 2012-05-23
> **goaliedude3919 said:**
> I've added the programs you suggested and through Psensor (hddtemp) it shows that my GPU is in the high 50's and low 60's while temp1 is at 25C and /dev/sdais at 36C. Could it be the GPU that is overheating?
 
Also, I have noticed that the overheating problem only occurs when my laptop is plugged in to charge. I can use it all I want unplugged and I have no problems, but it starts to get hotter when plugged in. This has never happened before. Is there a way to fix that?
 
It gets hot when plugged in because heat is a byproduct from the charging of the battery.
 
And my laptop won't even burn me, the fan will speed up so hard that it sounds like it's gonna take off (and i only succeeded in getting it that hot exactly once).

---

### Post by goaliedude3919 on 2012-05-23
> **2F4U said:**
> From the temperatures you post it looks as if the graphics card would be the problem. Which graphics driver are you using? The open source drivers are not as good in power management as the proprietary ones.
I'm not exactly sure. I had a whole bunch of different drivers installed from when I was trying to get Unity3D to work, so I'm not sure which drivers are in use. The GPU is an Nvidia though.

Just looking through the Software Center, it looks like I only have the "Additional Drivers (jockey-gtk)". Before I upgraded to 12.04, I had something like neavou drivers installed as well as something like version 92.

---

### Post by goaliedude3919 on 2012-05-24
Ok so the problem is definitely the GPU. I was watching the temperatures last night and the temps for the GPU would skyrocket whenever I did anything graphically taxing like watching a youtube video. The temps would jump up to the 90's, the fan would kick on, and it would drop back down to the 60's. I'm going to try cleaning out the fan and the heat sink and hopefully it's just dusty in there and that will fix the problem. If not, I'm just going to have to be very careful with how many videos I watch on this thing.

---

### Post by goaliedude3919 on 2012-09-03
I was able to resolve this issue by downloading the Bumblebee drivers to work with Optimus.

---

