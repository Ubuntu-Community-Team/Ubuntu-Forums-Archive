---
title: "Ubuntu 20.10 Nvidia RTX 2070 Max-Q crash"
date: 2021-01-04
forum: Hardware
---

### Post by gpaunescu2 on 2021-01-04
Hi all,

I have annoying issue with my laptop: MSI GS65 9SF.
Is my first laptop with RTX 2070; until now I had the same series (MSI GS65), but with 1060, 1070 and everything was fine.
I notice that I have freeze and crash quiet often, but after different investigation I'm sure that is because 2070 , when is under load and when become hot GPU.
Last few days I used an external cooler attached to GPU side; this kept low temperatures on GPU and I didn't have even single crash.
I have installed Nvidia driver 455.38 .
When it si crash is totally not responsive; even SysRq+Alt+REISUB not work; only I can shutdown from power button. It is very annoying.
I check on internet and seems that this is happen, but I didn't find a solution.
This is happen in Ubuntu gnome, unity and mate. Those I did try. Is my daily work machine and I cannot test another distros (but from what I've read is happen also in Manjaro).

If someone has some ideas please share with  me. 

Thanks,
Gabi

---

### Post by CatKiller on 2021-01-04
> **gpaunescu2 said:**
> I notice that I have freeze and crash quiet often, but after different investigation I'm sure that is because 2070 , when is under load and when become hot GPU.
Last few days I used an external cooler attached to GPU side; this kept low temperatures on GPU and I didn't have even single crash.
If it's crashing when it gets hot, and not crashing when it doesn't, then you have a thermal problem. If the machine is new, you could return it and swap it for a different machine that's better designed to handle its own heat.

If you want to keep that one, you'll need to take steps to give it adequate cooling. Ensure the vents are unobstructed. Use forced cooling when you can. Increase the fan speed. Consider improving the internal cooling arrangement with better thermal interfaces. Limit the power draw (and so generated heat) with nvidia-smi.

---

### Post by gpaunescu2 on 2021-01-04
Yeah sound like thermal issue, but something is not convince me.
The machine is one year old. (I did replace the thermal paste)
I read that there is some issue with 2070 and linux.
For me it took so long time to figure out because I was not able to find out in what conditions is crashing; I did suspect many combination of the applications.
But only recently I discover that also others complain about linux-2070 combination.
For example if only I play a game (like CS GO, Battlefield 4) is not happen nothing; the laptop fan is working and is some how hot but not freeze. 
More often is happen when I have more than one app that use GPU ( I had on the browser set to use GPU for example ) in the same time.
Also in furmark test don't go over 80-85 C degree (without external fan).
My big problem is that I don't know how to find some log related to the crash.
I will try to check what I can do with nvidia-smi (on the laptops is limited).

---

### Post by CatKiller on 2021-01-04
> **gpaunescu2 said:**
> I will try to check what I can do with nvidia-smi (on the laptops is limited).

If you have the option available, it will be something like

```
sudo nvidia-smi --power-limit=100
```

Obviously change the number (it's in Watts) to whatever heat level the chassis is able to exhaust. I use that sometimes (with a different number) if I'm protein folding, to limit how fast the fans have to turn.

---

