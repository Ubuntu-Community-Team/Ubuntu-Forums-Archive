---
title: "INSPIRON 6000 Battery"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by kaiserzoze on 2005-06-27
[COLOR=Red]ABOUT BATTERY LIFE INSPIRON 6000[/COLOR]


hello,
I suspect that my battery is not 100% ok, although I have my inpiron 6000 since 3 weeks.

Can someone post the results of

[COLOR=SlateGray]#cat /proc/acpi/battery/BAT0/info
#cat /proc/acpi/battery/BAT0/state[/COLOR]

I have a 9 cell battery (7200mA) the info file shows design capacity 7200mA, but the state file shows that the las full charge was 6880mA the first day I pluged my computer. Now, 3 weeks later, says 6840mA, I think this is a signal of battery degradation, but it is too soon!

*_What are your values? let's post them!_* (I do not have my laptop here, when I ve got I will post them)

Also in the /proc/acpi/battery/BAT0/state file when not AC pluged there is information about discharging rate, I get about 1700-2100mA with dimest screen light and doing 'nothing at all' wifi off.
My video card is ATI radeon X300, I use radeon driver as it supports "ATI powerplay" (option DynamicClocks="on" at /etc/X11/xorg.conf) but no great power battery savings with this enabled.


Thank you

---

### Post by kaiserzoze on 2005-06-27
As I said I post my battery information and state,
Please, send me yours as I could compare.
Thanks


[COLOR=SlateGray]kaiser@kaiserlinux:~$ cat /proc/acpi/battery/BAT0/info; cat /proc/acpi/battery/BAT0/state
present:                 yes
[B]design capacity:         7200 mAh
last full capacity:      6820 mAh[/B]<----the difference between design and last full capacity is increasing(battery degradation)
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL C54465
serial number:           11272
battery type:            LION
OEM info:                Sony
present:                 yes
capacity state:          ok
charging state:          discharging
**present rate:            1790 mA**<-----how could we decrease the discharging rate?
remaining capacity:      6800 mAh
present voltage:         12484 mV[/COLOR]

---

### Post by kaiserzoze on 2005-07-01
And the battery continues to decrease its capacity.....
no one has the same problem?

Please share yor battery status with me.
thks ;-)

design capacity:         7200 mAh
last full capacity:      6771 mAh ---------- it is getting worst!!
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL C54465
serial number:           11272
battery type:            LION
OEM info:                Sony
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      7200 mAh
present voltage:         12513 mV

---

### Post by jc3835 on 2005-07-01
Hello.
I have the 6-cell battery, so my capacity is lower than yours, but other than that maybe it'll help you out.

[INDENT]#cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         4800 mAh
last full capacity:      4800 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 480 mAh
design capacity low:     145 mAh
capacity granularity 1:  48 mAh
capacity granularity 2:  48 mAh
model number:            DELL F51335
serial number:           242
battery type:            LION
OEM info:                Sanyo

# cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      4800 mAh
present voltage:         12506 mV
[/INDENT]

JC

---

### Post by tflovik on 2005-07-02
Here's my battery info:

cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         7200 mAh
last full capacity:      7193 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL C54474
serial number:           439
battery type:            LION
OEM info:                Sanyo
tflovik@ubuntu:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1542 mA
remaining capacity:      4730 mAh
present voltage:         11560 mV

I have had the laptop since february and my battery is still good.
I can give you one advice. Use the battery until it is almost discharged befor you charge it. Plug the charger off when the battery is fully charged. I allways do this.

---

### Post by jc3835 on 2005-07-02
[QUOTE=tflovik]
I can give you one advice. Use the battery until it is almost discharged befor you charge it. Plug the charger off when the battery is fully charged. I allways do this.[/QUOTE]

That's not really necessary with LithiumIon batteries... they have no memory effect like the older NiCad or NiMH batteries did.
You're still welcomed to do that, but it won't help much.  ;-) 

JC

---

### Post by theccr2 on 2005-07-11
root@charles:/home/charlesr # cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         7200 mAh
last full capacity:      6940 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL C54475
serial number:           1213
battery type:            LION
OEM info:                Sanyo
root@charles:/home/charlesr # cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2261 mA
remaining capacity:      6120 mAh
present voltage:         12101 mV
root@charles:/home/charlesr #

i have had mine for almost a month and it is doing just fine for me

---

### Post by kaiserzoze on 2005-09-05
it is getting worst. I ask dell, they want to change my ac adapter, but not the battery right now.uhmmm it does not seem to be related with the adapter, anyway ... I still trying applying waranty for the battery. 

present:                 yes
design capacity:         7200 mAh
last full capacity:      6689 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL C54465
serial number:           11272
battery type:            LION
OEM info:                Sony
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1 mA
remaining capacity:      6674 mAh
present voltage:         12707 mV
kaiser@kaiserlinux:~/scripts$ bat
present:                 yes
design capacity:         7200 mAh
last full capacity:      6689 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL C54465
serial number:           11272
battery type:            LION
OEM info:                Sony
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1 mA
remaining capacity:      6674 mAh
present voltage:         12707 mV


How's your battery wear?

---

### Post by kaiserzoze on 2005-09-14
Latest news:

They changed my AC adapter, nothing new ... the battery last full capacity was the same.
So I asked Dell again and they send me a new battery holding 7192mA. this time, the battery _is a sanyo_ not a sony battery, this is the only difference (except the last full capacity ;-), of course ).

Well that's  the end of the story, or not ......

---

### Post by WaVeR on 2005-12-31
Some battery are defect:

Source: [https://www.dellbatteryprogram.com/Default.aspx](https://www.dellbatteryprogram.com/Default.aspx)

----8<------------8<--------
Dear Dell Customer,

In cooperation with the U.S. Consumer Product Safety Commission, Dell is voluntarily recalling and offering free replacements for certain notebook batteries that were sold for use with some models of Dell Latitude TM, Dell Precision TM and Dell Inspiron TM notebook computers. It is possible for these batteries to overheat, which could pose a risk of fire.

Potentially affected batteries were sold with the following models of Dell notebook computers or separately as secondary batteries:

    * Latitude D410, D505, D510, D600, D610, D800, D810
    * Inspiron 510M, 600M, **6000**, 8600, 9200, 9300, XPS Gen 2
    * Precision M20, M70
--->8------------>8---------

---

### Post by ronsgto on 2006-02-02
I am sorry but I don't know where to post this. I am actualy using Windows XP Home and am trying to find a way to monitor the battery. I seen post telling about acpi events. Is that just in linux? What programs are out there that can give this info.

Thanks for you patience.


Ron

---

### Post by ronsgto on 2006-02-02
[QUOTE=ronsgto]I am sorry but I don't know where to post this. I am actualy using Windows XP Home and am trying to find a way to monitor the battery. I seen post telling about acpi events. Is that just in linux? What programs are out there that can give this info.

Thanks for you patience.


Ron Keeping busy

---

### Post by ronsgto on 2006-02-02
How can I test the battery info, is there a program that you are using? I am using windows XP sorry if this is not the place to post this.

---

### Post by ronsgto on 2006-02-02
Actualy a question. What program can I use to test my battery. I am using windows xp sorry if this is not the place for this.

---

### Post by timseal on 2006-02-03
[QUOTE=ronsgto]Actualy a question. What program can I use to test my battery. I am using windows xp sorry if this is not the place for this.[/QUOTE]

Install Ubuntu and you might get some help here.

---

### Post by JensenDied on 2007-02-12
> **timseal said:**
> Install Ubuntu and you might get some help here.

wouldn't a live-cd work for his scenario? not sure if the acpi modules are loaded or not though.

anyway heres mine, so far worst battery here

jhornick@deathicide:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : 3278 mAh, 98.97%, 34:00:00
    Design capacity    : 4800 mAh
    Last full capacity : 3312 mAh, 69.00% of design capacity
    Capacity loss      : 31.00%
    Present rate       : 1 mA
    Charging state     : charging
    Battery type       : rechargeable, LION
    Model number       : DELL F51335
    Serial number      : 328

ive noticed that its remaining capacity shows 4800 when its full, even though it jumps instantly from ~3300 -> 4800 (yay me an 31%+ capacity loss)

the next two are done about 2 minutes apart to show whats happening

jhornick@deathicide:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : 4800 mAh, 100.0%, 03:54:31
    Design capacity    : 4800 mAh
    Last full capacity : 3312 mAh, 69.00% of design capacity
    Capacity loss      : 31.00%
    Present rate       : 1228 mA
    Charging state     : discharging
    Battery type       : rechargeable, LION
    Model number       : DELL F51335
    Serial number      : 328
jhornick@deathicide:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : 3276 mAh, 98.91%, 02:35:30
    Design capacity    : 4800 mAh
    Last full capacity : 3312 mAh, 69.00% of design capacity
    Capacity loss      : 31.00%
    Present rate       : 1264 mA
    Charging state     : discharging
    Battery type       : rechargeable, LION
    Model number       : DELL F51335
    Serial number      : 328

---

### Post by kd7swh on 2007-02-13
I have a similar problem with my D610. Dell is sending me a new battery tomorrow. (I had a sanyo battery that was not on the recall list, but it was still bad.) I hope our new batteries preform better.

:)

---

### Post by JensenDied on 2007-02-15
well i did some reading on the dell forums for batteries in general, apparently leaving the battery in while continously charging reduces its lifetime (basically what i do since i just use the battery as a sort of internal UPS on the notebook)

and since im reposting heres my new charge levels, dropped further (now below 2/3 capacity)

jhornick@deathicide:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : 4800 mAh, 100.0%, -1674:00:00
    Design capacity    : 4800 mAh
    Last full capacity : 3126 mAh, 65.12% of design capacity
    Capacity loss      : 34.88%
    Present rate       : 1 mA
    Charging state     : charged
    Battery type       : rechargeable, LION
    Model number       : DELL F51335
    Serial number      : 328

---

### Post by ephman on 2007-02-15
oooppppsss

---

### Post by ephman on 2007-02-15
i also have an inspiron 6000... my batt is one that needs to be recalled (about to do it)

ephman@wintermute:~$ cat /proc/acpi/battery/BAT0/info; cat /proc/acpi/battery/BAT0/state
present:                 yes
design capacity:         4800 mAh
last full capacity:      2952 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 480 mAh
design capacity low:     145 mAh
capacity granularity 1:  48 mAh
capacity granularity 2:  48 mAh
model number:            DELL F51326
serial number:           61982
battery type:            LION
OEM info:                Sony
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      4800 mAh
present voltage:         12503 mV

thanks for the bandwidth,

ephman

---

### Post by dasunst3r on 2007-02-15
Here's mine:
```
dasunst3r@hastalavista:~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         7200 mAh
last full capacity:      6828 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL D55516
serial number:           1605
battery type:            LION
OEM info:                SMP
dasunst3r@hastalavista:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      7200 mAh
present voltage:         12540 mV
```

(yes, I did name my computer "hastalavista" because I'm not touching Vista.)

---

### Post by nadeldave on 2008-02-12
My Dell Inspiron 6000 is 2.5 years old, the battery is terrible!

```

dave@dell-noodle:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : 100 mAh, 7.03%, 00:03:58
    Design capacity    : 7200 mAh
    Last full capacity : 1422 mAh, 19.8% of design capacity
    Capacity loss      : 80.2%
    Present rate       : 1512 mA
    Charging state     : discharging
    Battery type       : rechargeable, LION
    Model number       : DELL C54475
    Serial number      : 427
dave@dell-noodle:~$ 

```

---

### Post by f03el on 2008-03-06
Talking about terrible :(
```
  Battery #1     : present
    Remaining capacity : 672 mAh, 100.0%
    Design capacity    : 6000 mAh
    Last full capacity : 672 mAh, 11.20% of design capacity
    Capacity loss      : 88.80%
    Present rate       : unknown
    Charging state     : charging
    Battery type       : rechargeable, LION
    Model number       : Primary
    Serial number      :  

```
I don't know what has gone wrong with this battery in my 1.5 year old HP Pavilion dv6101. Perhaps the car adapter I have used is responsible? Anyway, just now I ordered a new 12 cell battery.

---

