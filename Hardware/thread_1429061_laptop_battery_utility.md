---
title: "laptop battery utility"
date: 2010-03-13
forum: Hardware
---

### Post by BrockStrongo on 2010-03-13
Hi All,
   Is anyone out there aware of a battery testing utility?
  I remember windows having a program that you ran off a usb key that took like six hours, but, completely reconditioned the battery.
   I ask because I just bought a new battery and gnome power manager says it is only reaching 77.1% of its intended capacity

Any thoughts?

---

### Post by Ante021 on 2011-01-18
Hi.

I see this is an old topic but I have to try. I have the same problem. Did you find a solution for that? Do you perhaps remember the name of windows program that reconditioned the battery? 

Thanx

---

### Post by yoramdavid on 2011-12-28
Same problem here, not only the command "cat info" tells me the capacity is only 49% of a 10 days old battery, but it is not charging any more.

---

### Post by Scott Baker on 2011-12-29
Pop into the software center and get the advanced battery monitor for laptops (ibam). I've used this on a few machines. It may cover the issues that you are having to deal with. (Incidentally, it will be found by opening the technical items section.)

---

### Post by Moozillaaa on 2011-12-29
Some batteries' BIOS monitoring needs occasional re-calibration.

Bring up BIOS/setup menu, battery power, and let it run OUT with no safety shutdown.

Then plug it in, and allow it to charge with EVERYTHING running. **The longer it takes to fully re-charge**, the better. Boot Windows, put in a DVD, plug in some USB devices, etc.

---

### Post by yoramdavid on 2011-12-30
> **Scott Baker said:**
> Pop into the software center and get the advanced battery monitor for laptops (ibam). I've used this on a few machines. It may cover the issues that you are having to deal with. (Incidentally, it will be found by opening the technical items section.)

Hi, is ibam a program with a gui?
I installed it and it did not add a launcher.
And trying to run if from the command-line I get an error:

```
ibam
terminate called after throwing an instance of 'std::ios_base::failure'
  what():  basic_filebuf::underflow error reading the file
Abortado

```

---

### Post by Scott Baker on 2012-01-10
Morning all. I recently recommended IBAM for monitoring laptops, but as of recent have found that it seems to be having problems ( seems to have started with 11.04 and 11.10 ). Right now, I wouldn't necessarily recommend it because of instabilities. Has anyone else noticed issues with this program? When it works, it works pretty well, but right now it seems to be crashing more than it should.

---

