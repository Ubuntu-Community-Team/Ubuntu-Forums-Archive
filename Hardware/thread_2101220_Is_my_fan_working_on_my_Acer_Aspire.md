---
title: "Is my fan working on my Acer Aspire?"
date: 2013-01-04
forum: Hardware
---

### Post by Pat500 on 2013-01-04
Hi all,
I have just purchased an Acer Aspire V3-571 (this model may only be available downunder (I'm from New Zealand) , as I haven't seen any posts on this particular model on this forum) and have put Ubuntu 12.04.1 16 bit on it. It has Windows 7 installed as well (it is dual boot). 
In my research on the Acer Aspire laptops, on this forum, I noticed that there were a lot of posts about the fan not working on many of these laptops. My laptop is very quiet, but I do hear a slight purring noise from it. I'm unsure though if this is just the hard drive spinning or if it is also my fan spinning. I know that when I boot up in Windows 7, it is also very quiet, but I think at times the fan kicks in, as I think that I hear it start to hum a bit louder sometimes. Also in Windows 7 the fan vent gets quite hot, whereas in Ubuntu it never does. I don't have any problems with the computer overheating though, it never shuts down, & the casing is quite cool, after it has been on for several hours, even  on the underside.
My question is: does anyone know how I can tell if my fan is actually working in Ubuntu? If it wasn't working, would my laptop shut down after a while from over heating?
Thank you all very much.    :)

---

### Post by adityamagadi on 2013-01-04
well you could try this 

[http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/)

---

### Post by Pat500 on 2013-01-05
Thanks for your reply but the Ubuntu version that the post that you linked to deals with Ubuntu version 9.10. As I am using version 12.04.1 the drivers have probably all changed, so I am nervous about using the fix you suggested. Thanks heaps anyway!
I found, by putting a small piece of tissue paper up against the inlet air vent, that the fan is working, for the tissue paper stuck to the vent, so the fan must be sucking in air. It's just very quiet, but hey rather quiet than noisy right?     :)
Thank you everyone.

---

### Post by adityamagadi on 2013-01-05
then your fan is runnig for sure :) o my bad ... you still have another option you can install a s/w called jupiter :

sudo add-apt-repository ppa:webupd8team/jupiter   

  sudo apt-get update 
sudo apt-get install jupiter

---

### Post by Pat500 on 2013-01-05
Thanks Adityamagadi. If I have further problems I'll give Jupiter a try.
Cheers.

---

### Post by adityamagadi on 2013-01-06
cheers :) jupiter displays your CPU temperature you can monitor the temperature variations and draw a conclusion about the fan :D

---

