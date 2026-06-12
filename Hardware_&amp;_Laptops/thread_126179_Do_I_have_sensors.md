---
title: "Do I have sensors?"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by andrewski on 2006-02-05
I've tried following the wiki [sensor howto]("https://wiki.ubuntu.com/SensorInstallHowto") for my Dell Inspiron 6000 but I haven't gotten it to work. I'm wondering if I really don't have sensors, but my sensors-applet does accurately detect my "THM" CPU temperature. Answering "yes" to all the defaults for the sensors-detect command, here's the output:
> **"sudo sensors-detect"] We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through said:**
>  
So the GNOME panel sensors applet is working. However, its package description does say that its flexible enough to gather its data from multiple sources, so I'm not sure that means anything:
[quote="sensor-applet description"]  * ACPI thermal zones
  * Linux kernel i2c, i8k, therm_adt746x, therm_windtunnel modules
  * lm-sensors
  * hddtemp daemon 
My lsmod searching shows that I have i2c_acpi_ec, i2c_core, and thermal installed.  And 'acpi -V' shows:
>      Battery 1: charged, 100%
     Thermal 1: ok, 32.0 degrees C
  AC Adapter 1: on-line (nice and cool :cool:). I read Wikipedia's article on ACPI, but I'm not really sure what it needs to work. So maybe I really don't have any sensor chips?

---

### Post by bluevoodoo1 on 2006-02-06
You could go into BIOS and see what readings there are? Then you'll know for sure what lm-sensors is capable of telling you. 

I've tried using that HOW-To and it was a pain, and it never worked. I just installed lm-sensors and sensors-applet with Synaptic and it worked perfectly. I'm using Breezy and it went without a hitch.

---

### Post by nanotube on 2006-02-07
hi,
i have a dell inspiron too. here is a link to my page that shows how I got my sensors working: 
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Temperature_and_Fan_Sensors](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Temperature_and_Fan_Sensors)
should work for you too.

---

### Post by andrewski on 2006-02-09
nanotube,
That page is great, for more than just the sensors.  I haven't had a chance to try it yet, but I will.  Just for curiosity, how many different sensors did you get with the i8k module?

---

### Post by nanotube on 2006-02-10
hey
with i8k, i have "cpu" "fan1" and "fan2"... although fan1 does not seem to be showing any info at all. (and i think i only have 1 fan ... :) ).

---

### Post by andrewski on 2006-02-10
(Yeah, that worked for me, down to the specifics.  What's with Fan 1? :))
Hmm, how would you feel about putting some of that more useful information in the Ubuntu wiki?  I'd be happy to help, if you're alright with that.

---

### Post by nanotube on 2006-02-11
hey andrewski,
glad it worked for you. :) 
as to posting some of the content on the ubuntu wiki: as you can see in the footer my wiki, all content is licensed under the GNU Free Documentation License. It (in short) allows you to freely copy, modify, and redistribute the contents, as long as proper attribution is made to the original creator of the document. 
the full gfdl can be found here:
[http://www.gnu.org/copyleft/fdl.html](http://www.gnu.org/copyleft/fdl.html)
so basically, i would certainly encourage you to feel free to put pieces of my howto into the official ubuntu wiki, as long as you make attributions to the original source (in the form of a link thereto).
feel free to pm me if you want to further discuss :)

---

