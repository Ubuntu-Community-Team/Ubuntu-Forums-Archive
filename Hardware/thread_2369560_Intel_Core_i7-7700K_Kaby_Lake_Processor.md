---
title: "Intel Core i7-7700K Kaby Lake Processor"
date: 2017-08-24
forum: Hardware
---

### Post by invektiv on 2017-08-24
I need a new processor and I'm thinking about buying the Intel Core i7 7700K processor.

At an online shop I saw that it only supports Windows 10 and that made me worry.

Is it that it only supports Windows 10 out of the different Microsoft systems? Or will it also be a problem running it under Ubuntu?

I only have Ubuntu and wanted to make sure this processor will work with Ubuntu before I bought it. Can you help me?
[h=1][/h]

---

### Post by anidxi on 2017-08-24
Hey!

From [here]("https://certification.ubuntu.com/catalog/component/dmi/4103/dmi%3AIntel%28R%29Core%28TM%29i7-7700CPU%403.60GHz/"), you can see that the Intel core i7-7700 is Ubuntu certified hardware. The 'K' at the end of the processor name is because the processor is overclockable AFAIK. From what I can see from the datasheets for the processors, they seem to use the same processor architecture. So, you shouldn't face issues with running Ubuntu on this particular processor. 

As far as what Intel has to say about Windows 10 - I think it's typical of what hardware manufacturers and OEMs do, like those "HP recommends Win 10" and such you see on advertisments - [here]("https://downloadcenter.intel.com/download/26836/Graphics-Intel-Graphics-Driver-for-Windows-15-45-?product=97129") you can see that Intel themselves have launched drivers for older versions of Windows, because the integrated graphics is shared with other processors.

Also, the processor microcode is available for linux [here]("https://downloadcenter.intel.com/download/26925/Linux-Processor-Microcode-Data-File?product=97129").

I hope this helps.

---

### Post by oldfred on 2017-08-24
I do not think cpu has ever been an issue.
Some issues with video cards in getting correct driver.
And some issues with various Wireless chips on getting correct driver.

If not a gamer then an i7 is probably overkill.
I am not a gamer, but my i5 Skylake is probably overkill. My fast system did not speed up my typing speed nor my Internet download speed.

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ) 

You can search pcpartpicker for example builds by checking types of hardware and then search on Linux.

---

### Post by Yellow Pasque on 2017-08-24
> **invektiv said:**
> Is it that it only supports Windows 10 out of the different Microsoft systems?

Yes, that. Kaby Lake is not officially supported on Win 7/8.x

---

### Post by invektiv on 2017-08-24
Thank you very much for your responses. They put my worries to rest.

---

