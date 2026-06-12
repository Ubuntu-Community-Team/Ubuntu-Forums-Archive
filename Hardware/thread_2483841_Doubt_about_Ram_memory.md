---
title: "Doubt about Ram memory"
date: 2023-02-10
forum: Hardware
---

### Post by ckrles on 2023-02-10
Hi. I've just bought a new intel nuc with 11th generation chipset. I'm running dual boot win10 and ubuntu 22.04.1 lts. Bios shows 8gb ram (2x4gb modules). Win 10 also detects 8gb, but my problem is with Ubuntu. If I go to settings>about it shows 4gb memory. However, if I run free -h in the terminal I get 7,4Gb. What information is wrong? What information should I trust? Ubuntu is running quite smoothly, so I suspect it's an error (possible bug) in the settings>about info.

Those two 4gb module were installed in my previous intel nuc and they were working fine. Only issue I see is that they are not the same. One is a Crucial module and the other one is Kingston. I can't tell if the frequencies are the same because on the Kingston it's not indicated.

I tried swapping the modules position in the slots, but the Nuc wouldn't boot. I guess that the first ram slot may take the lead when determining the frequency for the second module.

So, any ideas which of the two ram readins could be the right one and I should trust?

Thanks.

---

### Post by ajgreeny on 2023-02-10
See what output you get from ```
sudo lshw
``` particularly the memory section which should give us all the details of the two ram sticks inserted in your machine.

---

### Post by ckrles on 2023-02-11
I entered sudo lshw in the terminal. I think this is the relevant part of the output:

    *-memory
          descripción: Memoria de sistema
          id físico: 39
          ranura: Placa de sistema o placa base
          tamaño: 8GiB
        *-bank
             descripción: SODIMM DDR4 Síncrono 2400 MHz (0,4 ns)
             producto: KHX2400C14S4/4G
             fabricante: Kingston
             id físico: 0
             serie: C285708B
             ranura: Controller0-ChannelA-DIMM0
             tamaño: 4GiB
             anchura: 64 bits
             reloj: 2400MHz (0.4ns)


The output of vmstat -s -S M   is:

         7590 M memoria total
         1522 M memoria usada
         1183 M memoria activa
         2216 M memoria inactiva
         3337 M memoria libre
           95 M memoria de búfer
         2635 M caché de intercambio
         7720 M total de intercambio
            0 M intercambio usado
         7720 M intercambio libre
        31758 tics de CPU de usuario no-«nice»
          336 tics de CPU del usuario «nice»
        10600 tics de CPU del sistema
       902034 tics de CPU de inactividad
          906 tics de CPU de espera E/S
            0 tics de CPU de IRQ
          734 tics de CPU de softirq
            0 tics de CPU robados
      1855831 páginas en entrada
       514817 páginas en salida
            0 páginas intercambiadas
            0 páginas cambiadas
      2118051 interrupciones
      7198446 cambios de contexto de CPU
   1676111979 tiempo de arranque
        12084 bifurcaciones



I have a 4gb Kingston ram module and a 4gb Crucial ram module. I suspect it's only detecting the Kingston one. Am I right?

I don't understand it. Both Bios (UEFI) and Win 10 detect the two 4gb modules, but Ubuntu 22.04 doesn't. Any settings I need to adjust? If I interchange the ram in other slots, the Nuc won't boot. I'm a bit confused. Any ideas?
I read something about a part of the ram being saved for graphics. 
Thanks.

---

### Post by ajgreeny on 2023-02-11
Can you boot if you use just one of the two memory modules  trying first the Kingston, then swapping that for just the Crucial alone?
If they both work alone there must be some incompatibility between the two, though that is not something I can see any reason for.

There is a good system information script available for us a link to which I will find and you can then run it to see if if helps any more.
Back in a minute with the link.

Here it is.
[https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)
Download the script and run it in terminal and we can then try to see what extra info it gives us.

---

### Post by ckrles on 2023-02-11
The 2 ram modules are fine. The Nuc starts with each of the separately, but when combined only one is detected. If I swap the ram modules in the slots, the nuc won't boot. 
I have even tried another kingston 4gb ram from another pc and the result is the same. Only 4gb are detected in setting>about. However, Bios and Win 10 correctly show 8gb. I'm beginning to think it's a problem specific to ubuntu 22.04.1 lts and that the ram modules and slots are ok. In fact, Bios and Win 10 show the 8gb. So, I'm think about returning to Ubuntu 20.04 lts. Those two ram modules were being used in an older nuc running ubuntu 20.04 and they were recognised.

Any more ideas? It seems to be ubuntu-related.

---

### Post by ckrles on 2023-02-11
I don't know what's wrong. I've tried live booting Ubuntu 22.04.1 Lts (the one I have installled before and having ram issues with) and the result is exactly the same: only 4gb of out 8gb. However, if I live boot with a previous release, Ubuntu 20.04.5 Lts it correctly displays the 8gb ram available. I just don't know why. I'm afraid I'll have to go back to Ubuntu 20.04 which will be out of support in 13 months, in the hope that a new release or update of ubuntu recognises all ram.

---

### Post by TheFu on 2023-02-11
DDR4 RAM is sensitive to timing enough that I've had to reduce the speed when I put mismatched RAM - even the same model numbers - into the same system.  My 4 sticks of 3200Mhz RAM wouldn't boot until I forced the speed to be 2900Mhz and it wasn't stable until the speed was reduced to 2600Mhz.  With just 1 pair, it runs perfect at 3200Mhz.

So, I bought some match newer sticks and it has been running without any issues at 3200Mhz.

In short, for DDR4 RAM, only run matched RAM bought as a single kit.

BTW, the slightly less than 8G is because the CPU has an iGPU and that steals some RAM from the system.

For example, 2G is stolen for use by the iGPU/Radeon in my Ryzen APU, see:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            30G         19G        2.7G         94M        8.9G         11G
Swap:          4.3G        1.6G        2.6G
```

Here's the exact RAM inside:
```
$ sudo inxi -m
Memory:    Used/Total: 20694.2/31537.4MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: No Module Installed type: N/A
           Device-2: DIMM_A2 size: 16 GB speed: 3200 MT/s type: DDR4
           Device-3: DIMM_B1 size: No Module Installed type: N/A
           Device-4: DIMM_B2 size: 16 GB speed: 3200 MT/s type: DDR4

```

On another system, 
```

$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           14Gi       4.6Gi       790Mi       2.0Mi       9.4Gi       9.9Gi
Swap:         4.1Gi       737Mi       3.4Gi
$ sudo inxi -m
Memory:
  RAM: total: 14.75 GiB used: 7.82 GiB (53.0%) 
  Array-1: capacity: 128 GiB slots: 4 EC: None 
  Device-1: DIMM_A1 size: No Module Installed 
  Device-2: DIMM_A2 size: 8 GiB speed: 3200 MT/s 
  Device-3: DIMM_B1 size: No Module Installed 
  Device-4: DIMM_B2 size: 8 GiB speed: 3200 MT/s 

```
These are both using the same Ryzen APU model, in the same motherboard.  Note how the RAM stolen for the iGPU changes between the 16GB and 32GB system?  I suppose there's a way to control how much RAM is stolen in the MB BIOS.
I was thinking about adding another 16G, unmatched, to the smaller system.  I have those older memory sticks - same model as already installed. I'd expect to run at 2600Mhz to have a stable system.

Don't mix RAM lots, much less mix RAM models. Just don't.

Regardless, I've shown some commands you might find useful.

---

### Post by ckrles on 2023-02-11
Thank you very much for your help. You are right. DDR4 seems quite tricky and it may be a matter of mismatched speed (mhz). But I still don't understand  why it is faulty on ubuntu 22.04, and not on UEFI, Win 10 or Ubuntu 20.04.

I've moved back to Ubuntu 20.04 Lts where ram is shown correctly.
Thank you very much for your help.

---

### Post by Yellow Pasque on 2023-02-14
>  However, if I run free -h in the terminal I get 7,4Gb

I would trust that. I would not go back to Ubuntu 20.04 just because a GUI utility told me otherwise.

---

### Post by TheFu on 2023-02-14
> **Yellow Pasque said:**
> I would trust that. I would not go back to Ubuntu 20.04 just because a GUI utility told me otherwise.

+1!

---

### Post by aznnn on 2023-04-20
I've got the same problem on an [COLOR=#353535][FONT=Tahoma]NUC11TNHi50000.
Every system utils detects that I have 32 Gb of ram except for the "About" section.

The only weird thing is that the command

[/FONT][/COLOR]```
lshw -class memory
```[COLOR=#353535]
[FONT=Tahoma]Returns only 1 "Bank" but shows 32 Gbs as shown below 

[/FONT][/COLOR]```
  *-memory       description: Mémoire Système
       identifiant matériel: 39
       emplacement: Carte mère
       taille: 32GiB
     *-bank
          description: SODIMM DDR4 Synchrone 3200 MHz (0,3 ns)
          produit: CT16G4SFRA32A.M16FR
          fabricant: Crucial Technology
          identifiant matériel: 0
          numéro de série: E7E2D576
          emplacement: Controller0-ChannelA-DIMM0
          taille: 16GiB
          bits: 64 bits

          horloge: 3200MHz (0.3ns)
```[COLOR=#353535]


 
[/COLOR]

---

### Post by him610 on 2023-04-20
```
 sudo inxi -mxxz 
```

Trust that!

---

