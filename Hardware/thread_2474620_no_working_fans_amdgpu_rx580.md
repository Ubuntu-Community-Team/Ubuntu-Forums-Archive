---
title: "no working fans amdgpu rx580"
date: 2022-05-04
forum: Hardware
---

### Post by tuxer3322 on 2022-05-04
latest amdgpu or oibaf drivers makes the fan not to work,i have to do it manually to make the fans working by installing radeon-profile,could this be fixed please?this bug is new to me,at older releases the fan was working like nothing doing manually
please update amdgpu/1

---

### Post by Yellow Pasque on 2022-05-04
It's unlikely the oibaf PPA has anything to do with it. Try booting into an older kernel

---

### Post by pqwoerituytrueiwoq on 2022-05-07
the newer kernels have support for zero rpm mode if it is enabled in the vbios, that is probably what you are seeing, try putting the card under load and see if the fans spin up

note that removing this feature in the vbios will break uefi support

---

### Post by tuxer3322 on 2022-05-08
> **pqwoerituytrueiwoq said:**
> the newer kernels have support for zero rpm mode if it is enabled in the vbios, that is probably what you are seeing, try putting the card under load and see if the fans spin up

note that removing this feature in the vbios will break uefi support

So you mean that i must run a 3D application?

I have an ASUS mobo

Sometimes while browsing my display flickers cause of overheat i have a 4k monitor with display port,i can't save fan speed configuration in radeon-profile app,i set it to run startup

---

### Post by pqwoerituytrueiwoq on 2022-05-10
"So you mean that i must run a 3D application?"
no, it should just need the temperature to be high enough for the vbios to turn the fan(s) on, a 3d benchmark is a good way to get it warm

i noticed 0 rpm mode was suddenly supported in august 2021 when i updated the linux 5.11 kernel, i would expect the fans to run at all times on a kernel older than that

personally i do not like 0 rpm mode, i do not care if the core is at only 40C if the vrm and capacitors are at 60+, just give me a low fan speed to keep everything 20C cooler

on my 580 i changed the cooler out and i have 2 different fans ( [https://imgur.com/a/AOHDtRb](https://imgur.com/a/AOHDtRb) ) i have the small noctua fan's sense feeding the card, while the noctua fan supports 0 rpm the other does not and runs at 100% when told to, this is a wonderful safety to prevent a 0rpm mode from making anything overheat, if i use the larger fan for sense the card freaks out cause of the low rpm number and jumps it to 100% thinking there is a problem randomly, so the high RPM value of the NF-A4x10 PWM fan solves that issue, at the time linux has no 0 rpm support, it was great but when it was added rather than deal with software fan curves i managed to find generaleramon on overclock.net who was able to help me patch the bios in a hex editor and i was able to set a reasonable low fan speed and remove 0 rpm mode so i never have to deal with it again, sadly modding the bios breaks uefi boot support

---

### Post by tuxer3322 on 2022-05-12
I set the fan speed to 30%,just to cool the gpu but radeon-profile doesn't have a save button
When radeon-profile starts doesn't at startup doesn't make the fans to work,its says "auto" but fans don't work

---

### Post by pqwoerituytrueiwoq on 2022-05-12
this sounds like 0 rpm mode doing what it is supposed to do, i have no idea how to disable that feature in linux without using a full custom fan curve or hacking the vbios

radeon profile is basically a script that watches temperatures and sets a static fan speed every time the temp changes

---

