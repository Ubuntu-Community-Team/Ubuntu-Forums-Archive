---
title: "Amd Radeon graphics card causing problems"
date: 2021-01-05
forum: Hardware
---

### Post by maskedredstonerproz on 2021-01-05
As I mentioned in the title, the AMD Radeon graphics card on my laptop is causing me problems. It's freezing the screen suddenly out of nowhere, everything stops functioning, how do I know that's causing the problem? Simple, on windows, I fixed it by disabling my card's driver, disabling it in the process. When I switched to Ubuntu 20.04.1 LTS, the problem came back, ripping out the card is not an option, as it is soldered to the motherboard, the only possible fix is on the software level, what I am asking from all of you is if there's a way for me to do on Ubuntu, what I did on windows.

---

### Post by CelticWarrior on 2021-01-05
Welcome.

Do you have hybrid graphics?

---

### Post by maskedredstonerproz on 2021-01-05
Well, I think I do, I was shuffling through some settings bach when I had windows, and the integrated intel card was doing one half the job, while the amd radeon dedicated card was doing the other half, so I don't know what to tell you, hardware is not exactly my specialty, but I'm learning

---

### Post by maskedredstonerproz on 2021-01-06
> **CelticWarrior said:**
> Welcome.

Do you have hybrid graphics?

take a look at my post in the thread, I didn't find this option in time to use it properly, 
and I don't know how to delete the post

---

### Post by maskedredstonerproz on 2021-01-07
bump

---

### Post by CelticWarrior on 2021-01-07
With hybrid graphics you should enable the integrated graphics only if the goal is to bypass/disable the discrete graphics, not remove any driver.
However, the correct action is to repair the hardware itself if it's causing problems - thermal issues, perhaps? - after all you payed for it. If you don't need the better graphics you could have bought a much cheaper computer with only the Intel graphics.

In Windows the discrete AMD can be easily bypassed just by selecting the energy saving profile in the AMD software. High performance or on demand will enable the discrete AMD graphics, the former as always on and the latter just when needed by the software running at the time.

In Linux it's done by command line but I don't know which one.

---

### Post by maskedredstonerproz on 2021-01-07
> **CelticWarrior said:**
> With hybrid graphics you should enable the integrated graphics only if the goal is to bypass/disable the discrete graphics, not remove any driver.
However, the correct action is to repair the hardware itself if it's causing problems - thermal issues, perhaps? - after all you payed for it. If you don't need the better graphics you could have bought a much cheaper computer with only the Intel graphics.

In Windows the discrete AMD can be easily bypassed just by selecting the energy saving profile in the AMD software. High performance or on demand will enable the discrete AMD graphics, the former as always on and the latter just when needed by the software running at the time.

In Linux it's done by command line but I don't know which one.

I do not wish to remove the driver, just disable it, and as to why I didn't buy one with just Integrated intel graphics
I didn't have such an option, as to why my card is faulty, it's because a friend of mine fried it while
playing CS: GO with unoptimized settings

---

### Post by CelticWarrior on 2021-01-07
> [COLOR=#000000]I do not wish to remove the driver, just disable it[/COLOR]
Please read again what I wrote and try to understand it.

> [COLOR=#000000]it's because a friend of mine fried it while[/COLOR]
[COLOR=#000000]playing CS: GO with unoptimized settings[/COLOR]
Errr... No.
Clean the vents, heatsink, fans, replace the thermal paste... In a nutshell, take it to a professional.

---

### Post by Yellow Pasque on 2021-01-07
```
sudo apt-get install acpi-call-dkms
sudo modprobe -v acpi_call
```
Then see this for a script to turn the GPU off:
[https://wiki.archlinux.org/index.php/Hybrid_graphics#Using_acpi_call](https://wiki.archlinux.org/index.php/Hybrid_graphics#Using_acpi_call)

---

### Post by maskedredstonerproz on 2021-01-07
> **CelticWarrior said:**
> Please read again what I wrote and try to understand it.


Errr... No.
Clean the vents, heatsink, fans, replace the thermal paste... In a nutshell, take it to a professional.

already done it for Windows, can't now for linux plus I'm sure they got no clue about linux, 
btw the issue should be fixed now, I found a solution by posting more or less the same question in a linux
user group on Facebook

---

### Post by maskedredstonerproz on 2021-01-07
> **Yellow Pasque said:**
> ```
sudo apt-get install acpi-call-dkms
sudo modprobe -v acpi_call
```
Then see this for a script to turn the GPU off:
[https://wiki.archlinux.org/index.php/Hybrid_graphics#Using_acpi_call](https://wiki.archlinux.org/index.php/Hybrid_graphics#Using_acpi_call)

thank you kind stranger, I will make use of the provided resources if the problem re-emerges, 
so far everything is ok

---

