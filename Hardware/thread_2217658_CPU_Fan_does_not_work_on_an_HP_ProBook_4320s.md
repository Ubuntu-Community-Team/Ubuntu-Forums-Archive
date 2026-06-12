---
title: "CPU Fan does not work on an HP ProBook 4320s"
date: 2014-04-18
forum: Hardware
---

### Post by idodos on 2014-04-18
Hey everyone,

I have recently installed Ubuntu 14.04 and everything works great!
There's just one issue, it gets hot. Very hot.
It became quickly apparent that the fan does not work, it only works when the temperature reaches 90 degrees Celsius which is the max temperature according to the "sensors" command.
So it would run for a brief moment and have the temp go back to below 90, just to run again after a few seconds. The heat dispersion isn't half bad since it'll idle at 74-75c without a fan. lol
sensors-detect did not detect the fan. And so pwmconfig does not work either.
The fan works perfectly on Windows 7, and all the way through the boot process until I select Ubuntu in the grub menu, which is when it stops.

I will appreciate any help! : )

Thanks in advance!

---

### Post by chris-c on 2014-04-18
Hello,

I had quite a similar problem with my EliteBook 8440p, with the exception that the fan would neither work under Windows. I've managed to hack my fan after months of failures, and I'll try to get a post up with my experience when I have the time to do so. 

In the meantime to get your problem towards a solution, can you attach the disassembled DSDT table?
If you don't know how, you can refer to this page to get the DSDT.dsl file:
[http://linux.koolsolutions.com/2010/10/02/howto-faulty-acpi-bios-code-acpi-and-apic-issues-part-2/](http://linux.koolsolutions.com/2010/10/02/howto-faulty-acpi-bios-code-acpi-and-apic-issues-part-2/)

Also, If you feel comfortable experimenting with (and possibly doing something terribly bad to) your laptop, i've found this page while researching:
[http://www.tonymacx86.com/hp-probook/72043-new-fan-control-dsdt-silent-fan-higher-temps.html](http://www.tonymacx86.com/hp-probook/72043-new-fan-control-dsdt-silent-fan-higher-temps.html)

It's not for your series of laptops, but maybe you, or somebody more experimented than me on this forum, can figure out something.

Cheers!

EDIT:
Oh, and BTW, do try keeping your laptop cool, or your battery out! I've had to get a cooling pad for mine, but not after overheating my original battery to half capacity, so Head's Up!

---

### Post by idodos on 2014-04-18
Hey!

Thanks a lot for the reply.
Unfortunately, I cannot seem to find the dsdt file with the command in the article:
```
cp: cannot stat &#8216;/proc/acpi/dsdt&#8217;: No such file or directory
```
I've instead used:
```
sudo cat /sys/firmware/acpi/tables/DSDT > DSDT.dat
```

Don't know if it makes a difference.

So here's the file: [ATTACH]252174[/ATTACH]


The second link you've sent me, I don't really understand.. It seems to be referring to a macos install.

Also, I think I was able to slightly reduce the temp using:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
``` in etc/default/grub

Not sure if the fan works now, if it does then it's on a very low rpm.


Thanks a bunch for attempting to help me with this issue!

---

### Post by chris-c on 2014-04-18
[I]I realized that in my eagerness I forgot the obvious:
[B]First things first:
[/B]
The first thing you should try, if you haven't already, is the lm-sensors package.
```
sudo apt-get install lm-sensors
```
then
```
sudo sensors-detect
```
and follow the instructions to search for a fan controller module.

If you, like me, didn't have any luck and the script didn't find anything other than the coretemp module, time for the next step:
[/I]EDIT:
Yes... What writing a post inbetween housework means. Sorry, I only now read that you've already tried this. :oops:
[B]
The tricky part[/B]

Your fan control methods are identical to my EliteBook, I'll be able to explain what they do and hopefully come to a solution.

[B]Now for the disclaimer:
[/B]1. Although your control methods are identical to mine, it's not the same laptop, and I have no **guarantee** you won't break anything. The instructions should be completely safe (in other words, should not do anything a battery unplug won't solve/reset) and were safe for my situation. Realistically, nothing bad should happen, but with only one laptop to test them on, I can't know for sure. I hope you are happy with that moving on.

2. There may be other ways to solve the problem for your laptop. There weren't any for mine. If you're not completely happy with the above you should probably wait for somebody with more experience than me.

Ok, with that out of the way, we'll try to inch towards a solution.

1. Install the acpi_call module.
acpi_call is a very crude kernel module that enables direct calling of ACPI methods, and it's mainly used to turn on/off discrete GPU's, but we're not using it for that.
To reduce copy-pasting here is a guide for its installation:
[http://abz89.wordpress.com/2012/11/26/disabling-discrete-gpu-in-most-linux-system/](http://abz89.wordpress.com/2012/11/26/disabling-discrete-gpu-in-most-linux-system/)

You should follow it up to, but not including step **7. Test it**. We're not interested in GPU's and don't want to break anything so just make sure that /proc/acpi/call exists.
To make it start every time you boot you can do ```
sudo echo acpi_call >> /etc/modules
```.

2. Check the ACPI methods.

From what you're saying, it seems that the OS is controlling the operation of the fan, as in my case. What happened to mine was that even under Windows 7, the fan would only operate if the "Fan always on while on A/C" option was checked in the BIOS, while under Ubuntu, nothing would happen. 

These are the functions related to fan control, as I have understood them. We'll get around to playing with them with acpi_call later:
```

Method (KFCL, 2, NotSerialized)
{
    Acquire (ECMX, 0xFFFF)
    If (ECRG)
    {
        Store (Arg1, MFAC)
        If (LAnd (LGreaterEqual (Arg0, 0x00), LLessEqual (Arg0, 0x64)))
        {
            Store (Arg0, CFAN)
        }
    }


    Release (ECMX)
}

```
**KFCL**. I don't know exactly what it means, but it needs 2 arguments, which it stores in *MFAC* and *CFAN* in the Embedded Controller of the laptop.
In my case, whatever I put in CFAN would get overwritten 100ms later, but *MFAC* would stay and power the fan while my laptop was on AC power. 


```

Method (KSFS, 1, NotSerialized)
{
    Acquire (ECMX, 0xFFFF)
    If (ECRG)
    {
        Store (Arg0, CFAN)
    }


    Release (ECMX)
}

```
**KSFS**. *K Set Fan Speed*, I think. It takes one value and stores it in *CFAN* for the controller to use. On my laptop it was overwritten 100ms later, but you may have better luck.

```

Method (KGFS, 0, NotSerialized)
{
    Store (0x14, Local0)
    Acquire (ECMX, 0xFFFF)
    If (ECRG)
    {
        Store (CFAN, Local0)
    }


    Release (ECMX)
    Return (Local0)
}

```
**KGFS. ***K Get Fan Speed*. This reads the target fan speed from the controller.

```

Method (KRFS, 0, NotSerialized)
{
    Store (0x1E, Local0)
    Acquire (ECMX, 0xFFFF)
    If (ECRG)
    {
        Store (PFAN, Local0)
    }


    Release (ECMX)
    Return (Local0)
}


```
**KRFS***. K Read/Real? Fan Speed*. This reads the actual speed of the fan, which is not completely stable and revolves a few RPM's around the Target fan speed (The one in **KGFS** as set by **KSFS**).

Now, these functions belong to a device, in a region. If you follow the DSDT file from the functions up top, you'll notice they are under "\_SB.PCI0.LPCB.EC0"

Now that we know where the functions that we want are located, it's time to explain a bit how acpi_call works, assuming you have installed it.
You write the function/variable you want to check into the /proc/acpi/call file and then read it to get the result. For example:
```

echo "\_SB.PCI0.LPCB.EC0.KRFS" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
Would display the result of our K ReadFanSpeed function (i.e. the actual fan speed)

OR
```

echo "\_SB.PCI0.LPCB.EC0.KSFS 50" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
Would call the KSetFanSpeed function with its first argument as 50, thus turning on/off the fan at your desired speed.

So, to test if these functions work for you:

1. Open up a terminal and get yourself root access:
```
sudo su
```
2. Get yourself ready to check if the physical fan is spinning, either with a piece of cloth/napkin over the fan hole or by placing your ear and listening.
3. Check each function as follows:
The easy ones:
```

echo "\_SB.PCI0.LPCB.EC0.KRFS" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
This should read 0x0 if the fan isn't spinning, otherwise your problem isn't exactly like mine, in which case stop and we'll explore other avenues (The problem isn't here)
0x0 is just hexadecimal for 0.
```

echo "\_SB.PCI0.LPCB.EC0.KGFS" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
This should also read back 0x0 if the fan isn't ordered to spin. If it's not, see the above.

Now, the fan isn't spinning, and we can read what the embedded controller thinks the fan is doing. Let's give it something to do:

```

echo "\_SB.PCI0.LPCB.EC0.KSFS 50" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
We're calling the KSetFanSpeed function and also giving it a variable, 50. This should spin the fan up at 50% or whereabouts. Check with a cloth/napkin/ear if the fan is spinning
If it does nothing, or the fan stops after less than a second, your problem is like mine and i'll continue in another post.
If it stays spinning, we'll figure out a way to automate this command.

Lastly, what saved my laptop while investigating the problem was the KFCL command. If the above doesn't work, you can at least make the fan run continuously while on AC power.
```

echo "\_SB.PCI0.LPCB.EC0.KFCL 0 30" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```

This function takes 2 arguments. The first argument is stored in CFAN, like KSFS, and if the above did nothing, we're not interested in giving it anything, thus, 0.
The second argument is stored in MFAC, and on my laptop it told the controller what speed the fan should be while connected to the charger. Place any suitable number from 1 to 100 instead of 30, so your fan won't overheat while we figure this out.

Also, you need to repeat this last command every time you restart linux, otherwise the controller will forget this value.

Awaiting your reply!

P.S. I was writing this in batches and may have missed something, sorry if it's not as clear as it could be and please question everything you don't know before actually taking any actions.

EDIT:
Corrected the path in the ACPI commands to include EC0.

---

### Post by idodos on 2014-04-18
Hey,

Well I've installed the acpi_call module and it is active as shown by "modinfo acpi_call:
```
root@HP-ProBook:/home/ido# modinfo acpi_call
filename:       /lib/modules/3.13.0-24-generic/updates/dkms/acpi_call.ko
license:        GPL
srcversion:     981F71E01A503AE1931E3A1
depends:        
vermagic:       3.13.0-24-generic SMP mod_unload modversions 

```

However, all of the echo commands return the same output:
```
Error: AE_NOT_FOUND
```

Any idea as to what exactly I am doing wrong?

---

### Post by chris-c on 2014-04-18
Ok, this is getting more embarrassing by the minute.
I copied the code from my script without checking the full path of the ACPI command (remember the "\_SB.PCI0.LPCB.EC0" thing?, the commands I posted lack the EC0 part.)

```

Error: AE_NOT_FOUND

```
Means it didn't find the requested item (No harm done)... and it couldn't have because of my mistake. Sorry again.

I will edit my post with the correct commands. Instead of
```
echo "\_SB.PCI0.LPCB.<COMMAND>" > /proc/acpi/call && echo $(cat /proc/acpi/call)
```
the correct path is
```
echo "\_SB.PCI0.LPCB.**EC0.**<COMMAND>" > /proc/acpi/call && echo $(cat /proc/acpi/call)
```

---

### Post by idodos on 2014-04-18
Hey, no worries : )

And it works!
Exactly as you said it would. The first 2 commands return 0x0.
The third command (KSFS) gets the fan spinning for a moment before it turns off again.
And the fourth command (KFCL) works as you said.

Thanks a lot!
So basically what you do every time is have the fan set to 30% fan speed?
It's not ideal but at least it works. Isn't there a way to have Ubuntu use this command to set the fan speed instead of whatever else it is using?

Again, thanks a lot. I've searched for a solution for a while and never found anything similar to your solution!

---

### Post by chris-c on 2014-04-18
Alright. 
> Thanks a lot!

So basically what you do every time is have the fan set to 30% fan speed?

You're welcome and I'm glad I could help.
And regarding the 30% fan speed: Not exactly.
30 is a number I pulled out of thin air to test it. Any number you see fit between 1 and 100 works. This depends on how silent/loud you want the fan, how cool you want it to be, etc. and only works while plugged in.

This is only the first part of the solution, and only works while plugged in. This is how I lived for a couple of months :D
For a more workable, but still temporary solution (I'm in the midst of building a kernel module to automatically control this):
We need to see if you have the same fan controller chip (the only one I know to operate) and
We need to create a script to take care of checking the temperature and setting the correct fan speed.

And... this is where things are different for our two laptops.
First, your fan control chip is at a different address (0x99 vs my 0x5D) and we'll need to check if it's still the same controller.

Execute this code (I've double checked it now :D):
```

echo "\_SB.PCI0.LPCB.SMAB 0x99 0xFE" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
and then
```

echo "\_SB.PCI0.LPCB.SMAB 0x99 0xFF" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
And tell me the output for each one. We're now talking directly to (hopefully) the fan controller chip (from your DSDT file I see it's at address 0x99) and asking it's Manufacturer (argument 0xFE) and Model/Revision (0xFF)

Here's my output (my controller is at 0x5D):
```

root@PortableMe:/home/cristian# echo "\_SB.PCI0.LPCB.SMAB 0x5D 0xFE" > /proc/acpi/call && echo $(cat /proc/acpi/call)
0x5d
root@PortableMe:/home/cristian# echo "\_SB.PCI0.LPCB.SMAB 0x5D 0xFF" > /proc/acpi/call && echo $(cat /proc/acpi/call)
0x81

```

If the output is exactly the same, you can safely execute this:
```

echo "\_SB.PCI0.LPCB.SMAB 0x99 0x50" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
and tell me the output.

Otherwise, I'll try to figure out what fan controller you have based on the 2 outputs.

---

### Post by idodos on 2014-04-18
Here:

```
root@HP-ProBook:/home/ido# echo "\_SB.PCI0.LPCB.SMAB 0x99 0xFE" > /proc/acpi/call && echo $(cat /proc/acpi/call)
0x5dalled
root@HP-ProBook:/home/ido# echo "\_SB.PCI0.LPCB.SMAB 0x99 0xFF" > /proc/acpi/call && echo $(cat /proc/acpi/call)
0x3called

```

Weird, the output I get is *alled while yours does not have the "alled" part.

This is true for any echo I issue, see:
```
root@HP-ProBook:/home/ido# echo "\_SB.PCI0.LPCB.EC0.KRFS" > /proc/acpi/call && echo $(cat /proc/acpi/call)
0x1ealled

```


Anyways, it's not like yours. So what now? :D

---

### Post by chris-c on 2014-04-18
the "called" part has to do with how acpi_call is programmed.
Every time you read from the /proc/acpi/call file it's contents are refreshed, so if you read the file without previously issuing a command, it reads "not called"... but when you issue a command and it returns, it just overwrites that "not called" string, it doesn't replace it. I've modified my acpi_call source code and replaced the "not called" strings with empty ones so I could see the results better, but it's no worry.

The first result, 0x5D means it's still a microchip controller, just a different model (0x3C, i assume). I'll just have to find what the chip with 3C is online and check what the differences are. I'll post when I have the datasheet for it.

Hang on tight! :D

---

### Post by idodos on 2014-04-18
Coolio.

I'm glad there's someone who's capable of helping me with this. To be honest, I don't really understand much about how exactly acpi works.
Strange that this issue was never resolved, but it seems to only effect old (2-3 years) hp laptops. From what I've read anyways.
So maybe Ubuntu developers don't really care. lol

---

### Post by chris-c on 2014-04-18
Hmm...

I think I've misunderstood the second result. It doesn't seem to be the model ID per se, but only the revision of the model.
To find out the exact name of the chip I'll need your help.

There are two ways of doing this:
[I]
The Easy Way[/I]
If you still have Windows installed, grab this great little piece of software:
[http://www.hwinfo.com/](http://www.hwinfo.com/)
Install it, and run it.

Check "Sensors Only" when it prompts you:
[IMG]http://i.imgur.com/qFMzZb0.png[/IMG]

And then look in the table it gives you for something like this:
[IMG]http://i.imgur.com/nMxZDg5.png[/IMG]

It may or may not have a Fan attribute, as it only detects it if it's running, but it should start with SMSC if we're lucky.

If not, tell me all the items that have the same icon and we'll see.
[I]
The Void-My-Warranty Way
[/I]This is a tad harder... and **will VOID YOUR WARRANTY**, if you have one.

The basic idea is to look on all the motherboard chips for any that say SMSC on them. Don't get me wrong, that chip is TINY. Here's what mine looks like:
[IMG]http://i.imgur.com/LZhmnJ1.png[/IMG]

As you can see, my fan controller is an SMSC 2113-1.

You will have to pop open the keyboard (You'll have to look online how to do that) and carefully, not to pry off any cables.

If anyone else has any idea how to get the model number, please share!
Otherwise,
Good luck!

---

### Post by idodos on 2014-04-18
Still have Windows.
I have disassembled the laptop before however, but I chose the easy way for now.

**SMSC EMC1402**

No fan attribute. Hopefully this will help you figure it out! : )

---

### Post by chris-c on 2014-04-18
No good.
That device is only a temperature sensor.

D'oh!
Check out what the datasheet says.
FDh Product ID Stores the unique Product ID
FEh Manufacturer ID
FFh Revision Number

We've only looked up FE and FF... fire up the root command prompt again
```

sudo su

```
```

echo "\_SB.PCI0.LPCB.SMAB 0x99 0xFD" > /proc/acpi/call && echo $(cat /proc/acpi/call)

```
And see what chip we're talking to.

If the output is **0x20 **then we are talking to the temperature sensor and not the fan controller.
That means one of two things:
1. There must be another chip at another address, i'll have to check the DSDT again and more thoroughly
2. Your fan in controlled by the Embedded Controller directly, in which case I can't help you any more than I already have.

I'll start browsing the DSDT now, tell me what you have.

---

### Post by idodos on 2014-04-18
Yep, the output is **0x20alled**

If it'll help, I could open the laptop to check for another controller. Think there's a chance?

Edit:
Went for it. I can't find any "smsc" chip. Where should it be?

---

### Post by chris-c on 2014-04-18
Ok, this is weird.
The DSDT is identical to mine in the fan control aspects, which leads me to believe the SMSC EMC1402 is wrongly identified.
If you're ok with this, we'll go in blind and try to figure things out as if this is the fan control chip.

I've been busy refreshing my bash to write you a script.
```

#!/bin/bash


acpi_call () {
    echo "$*" > /proc/acpi/call
    echo "$(cat /proc/acpi/call)"
}


read_byte () {
    CMD="\_SB.PCI0.LPCB.SMAB 0x99 0x$1 0x00"
    echo "$(acpi_call $CMD)"
}


decToHex () {
    echo "$(printf "%.2x" $1)"
}


STR=""
for i in {0..256}
do
    echo -en "\rReading Byte $i"
    STR+="$(read_byte $(decToHex $i)) "
    if ((i%16 == 15)); then
        STR+="\n"
    fi
    # sleep 1
done
echo -en "\rDone               \n"
echo -en $STR

```

Copy the above code in a file, name it something like fancheck
then go to the directory where you saved it and execute
```
sudo ./fancheck
```
Paste the output here.

We might still have a chance!
:D

---

### Post by idodos on 2014-04-18
Reassembling laptop.
All I found was a RT8152C which appears to be a PWM controller for the CPU.
All the rest were unidentifiable. At least for me.

---

### Post by idodos on 2014-04-18
Here:

```
ido@HP-ProBook:~$ sudo ./fancheck
Done               
0x25alled 0x25alled 0x0called 0x0called 0x4called 0x7falled 0x0called 0x7falled 0x0called 0x0called 0x4called 0x7falled 0x0called 0x7falled 0x0called 0x0called 
0x40alled 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x7falled 0x0called 0x0called 0x0called 0x0called 0x0called 0x3called 
0x7falled 0xacalled 0x70alled 0x0called 0x0called 0xfcalled 0x0called 0x12alled 0x0called 0x60alled 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x6called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x6called 0x7called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x65alled 0x40alled 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x2balled 0x12alled 0x6called 0x50alled 
0x20alled 0x20alled 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 
0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x0called 0x20alled 0x5dalled 0x3called 

```

---

### Post by chris-c on 2014-04-18
Bummer.

It *IS *just a temperature sensor.
This leaves just the Embedded Controller, and only two more functions, which I don't completely understand.
```
Method (SFSD, 1, Serialized)
{
    Multiply (Arg0, 0x40, Local1)
    Divide (Local1, 0x64, Local2, Local0)
    Subtract (0x40, Local0, Local0)
    And (PWM0, 0x80, Local1)
    If (LEqual (Local0, 0x40))
    {
        Or (Local1, 0x01, Local1)
    }
    Else
    {
        ShiftLeft (Local0, 0x01, Local0)
        Or (Local0, Local1, Local1)
    }


    Store (Local1, PWM0)
}
```
**SFSD**. *Set Fan Speed Direct/Decimal?*. Takes one paramter, does some magic to it and stores it into a PWM variable...



```
Method (GFSD, 0, Serialized)
{
    And (PWM0, 0x7F, Local0)
    If (And (Local0, 0x01))
    {
        Store (0x00, Local1)
    }
    Else
    {
        ShiftRight (Local0, 0x01, Local0)
        Subtract (0x40, Local0, Local0)
        Multiply (Local0, 0x64, Local0)
        Divide (Add (Local0, 0x20), 0x40, Local2, Local1)
        Increment (Local1)
    }


    Return (Local1)
}
```
**GFSD**. *Get Fan Speed Direct/Decimal?*. Returns the PWM variable after some magic.

You may try
```
echo "\_SB.PCI0.LPCB.EC0.SFSD 0xXY" > /proc/acpi/call && echo $(cat /proc/acpi/call)
```
as root (sudo su)
with 0xXY one of: 0x1, 0x80, 0x81, or others you may think of. See what happens to the fan.

I haven't had any luck with these, though.
The fan would spin only to reach the target speed, but when it would need to keep stable it would turn off.
It spun as if only while ramping up speed.

If your fan manages to keep the speed stable after ramping up, we might finally have an answer.

Otherwise, I'm sorry. This is the last think I can think of.

Good luck!

---

### Post by idodos on 2014-04-18
```
echo "\_SB.PCI0.LPCB.EC0.SFSD 0xXY" > /proc/acpi/call && echo $(cat /proc/acpi/call)
```

Works. Fan keeps stable.
It was difficult at first, but with 0x100 I can clearly feel and hear the fan working.
"KRFS" returns 0x0 when the fan is working with "SFSD".
So what exactly does 0xXY mean in terms of actual fan percentage?

Edit:
Seems like GFSD returns the actual fan speed in hex. So a value of 0x80 in SFSD is 28% and 0x100 is 56%.

---

### Post by chris-c on 2014-04-18
I don't know yet what it means in terms of percentage. It didn't work for me and I didn't check it further.

I'll check it tomorrow. Until then,  you have to manage with what you have.

Cheers! :)

---

### Post by idodos on 2014-04-18
Alright, thanks a bunch! : )
And if you haven't seen the edit, GFSD appears to return the actual fan speed value in hex.

Thanks again and have a good night!

---

### Post by chris-c on 2014-04-19
Alright, 
Sorry for the long wait, but as you can see, I've been busy. :D

I've had a look through the SFSD/GFSD methods.
And... I don't quite understand them fully yet.
```
SFSD (Input) {
    InputInverted = 64 - (Input*64)/100;
    Local1 = PWM0 && 128; // Either 128 or 0 (Local1 to PWM0's bit7)
    if (InputInverted == 64) { // If The fan speed(Input) is set to 0
        PWM0 =  Local1 || 1; // 129 or 1; sets the first bit to 1 and bit 7 to PWM0's
    } else {
        PWM0 = (InputInverted * 2) || Local1
        // bit 7 is either what PWM0 had at the beginning, if that bit is set
        // or InputInverted's, if that bit is set...
        // How do you set it to 0?!
    }
}
```
This takes an input from 0 to 100 (0x0 to 0x64), scales it to 0-64 (0x0-0x40) then subtracts it from 64, giving an inverted range from 64(fan off?) to 0 (fan full sp?)


This is where things get interesting. If the Input==0, PWM0 has its first bit set to 1 and the rest unchanged. 
Presumably, then, the first bit of PWM0 is 0 for fan active and 1 for fan off? It could also mean automatic control (1) vs manual control (0)?...


Ok, if Input isn't 0, InputInverted gets shifted left (*2) and its bit 7 is set to whatever PWM0 had at the beginning, if Input<64 or 1 if input >=64. How do you turn it back to 0?!


Onwards!
```
GFSD () {
    Local0 = PWM0 && 127 // Local0 to PWM0, ignoring bit 7
    if (Local0 && 1 != 0) { 
        // If the first bit is 1, speed=0
        return 0; 
    } else {
        // First bit isn't 0, shift Local0 right (discard first bit)
        // and reverse procedure to find fan %
        Local0 = 100 * (64 - (Local0 / 2)); 
        return ((Local0 + 32) / 64) + 1;
    }
}
```


Alright. It seems bit 7 of PWM0 is something SFSD can only set to 1, and the first bit is fan on/off.
That leaves us with 6 bits or 63 levels of fan control.
That means that before conversion, SFSD expects numbers from 0 to 99. Everything above should set bit 7 to 1, and god knows what that does!
Or did I get something wrong?


Onwards!
Here's a debug script to better see what's happening
Oh, before that:
You need to modify your acpi_call to get rid of the *alled part, or it'll break the script.


Go to:
```
cd /usr/src/
```
Make a new directory:
```
sudo mkdir ./acpi_call-0.0.2
```
And copy the contents of the previous version
```
sudo cp ./acpi_call-0.0.1/* ./acpi_call-0.0.2
```


Open the acpi_call.c file from v 0.0.2 with the editor of your choice
```
sudo gedit ./acpi_call-0.0.2/acpi_call.c
```


Find and replace every occurence of the string "not called" with a space: " "
```
ex: 
strcpy(result_buffer, "not called");
becomes
strcpy(result_buffer, " ");
```


Save it, then open dkms.conf in the v0.0.2 folder and replace the 2 occurences of "0.0.1" with "0.0.2".


Then build the new version like you did the first one
```

sudo dkms add -m acpi_call -v 0.0.2
sudo dkms build -m acpi_call -v 0.0.2
sudo dkms install -m acpi_call -v 0.0.2

```
And I THINK by
```

sudo modprobe -r acpi_call
sudo modprobe acpi_call

```
you should load the new version, I can't remember how I did it.
Hopefully it works for you.
EDIT: I've tried the commands, they seem to be working for me

To test if you have the right version
```
sudo cat /proc/acpi/call
```
Should give you an empty string, and not "not called".


Now, the script:
```
#!/bin/bash
# 
# HP ProBook 4320s Fan Control
# DEBUG Script
# V 0.0.1
# PWM0 Debug


# Make sure only root can run our script
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi


# Make sure acpi_call is installed
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi


# acpi_call helper method
acpi_call () {
    echo "$*" > /proc/acpi/call
    echo "$(cat /proc/acpi/call)"
}


# echo -en "\033[8;5;20t"
echo -en "\033]0;Fan Control DEBUG\007"


while true; do
    #Directly extract the PWM0 variable
    PWM0h=$(acpi_call "\_SB.PCI0.LPCB.EC0.PWM0"|cut -b3,4) # hex
    PWM0b=$(echo "obase=2; ibase=16; ${PWM0h^^}" | bc )    # binary
    PWM0d=$(echo "obase=10; ibase=16; ${PWM0h^^}" | bc )   # decimal
    
    echo -en "\ec" # Clear terminal
    echo -e "HP ProBook 4320s DEBUG script"
    echo -e "-- PWM0 -------"
    echo -e " hex: $PWM0h"
    echo -e " bin: $PWM0b"
    echo -e " dec: $PWM0d"
    echo -e "-- Fan --------"
    echo -e "  Fan Off: $(($PWM0d & 1))"
    echo -e "    Bit 7: $((($PWM0d & 128) >> 7))"
    SPD=$((($PWM0d & 127) >> 1))
    echo -e "Fan Speed: $(( 100 - ($SPD*100)/64 ))%"
    sleep 1
done
```


paste this in a file, let's say pb_debug, execute it in a terminal with
```
sudo ./pb_debug
```
then open a new root terminal (sudo su), place the two side by side and play with the SFSD command
See if you can tell me what bit 7 seems to do.
EDIT: Be sure to try it with the charger plugged in, as well as unplugged. See if that makes any difference.

If bit 7 is stuck, you may have to reset the EC.
Here's how (Don't worry about the Mac OS thing, it's the same hardware :) )
[http://www.tonymacx86.com/hp-probook/106177-ec-reset-embedded-controller-reset-sticky-probook-ec-reset.html](http://www.tonymacx86.com/hp-probook/106177-ec-reset-embedded-controller-reset-sticky-probook-ec-reset.html)


Let's see if this gets us anywhere!
Until we understand these commands fully, any script we write for them won't be sure to work as intended.

---

### Post by idodos on 2014-04-19
Alright, did some tests.
Bit 7 never seem to change, always remaining "1".
Disconnecting ac also doesn't seem to make a difference.
"Fan off" works as intended, that is, it's "1" when fan is off.
And fan is off using either 0x0 or 0x1.
Also, when fan is off, fan speed shows "100%", but that's probably just an issue with the script.

Is this good or should I test something else? lol


Edit:
Ops forgot to do that ec reset thing, will do so now.

Edit 2:
Nope, Bit 7 remains "1".

---

### Post by chris-c on 2014-04-19
Alright. Sounds good.
What about the fan speed control? Does that work as intended?
I'm interested in whether it shows 40% when you do [...].SFSD 40 and whether the fan actually spins loudest at SFSD 99.
Do you have to go over 100/0x64, like you said an earlier post with ... 0x100, i believe?

---

### Post by idodos on 2014-04-19
It works well, 0x64 and 0x65 seem to set the fan to 100%
Same as 0x0 and 0x1 sets it to 0%.
And then 0x66 sets the fan to 2% and so on.
0x100 is 55% 0x129 is 97% and 0x130 is 4%
Yeah it's pretty weird.
Guess it would be the simplest to work with 0x0-0x64

Edit:
And you've asked about 0x99 which is 52%

---

### Post by chris-c on 2014-04-19
When you call the SFSD method, 0x64 is not the same as 64.
That 0x prefix tells acpi_call to expect a value in hexadecimal. If it's not there it expects a decimal number.
SFSD 64 is the same as SFSD 0x40. (40 in hexadecimal = 64 in our run-of-the-mill decimal)
0x64  = 100
0x66   = 102
0x100 = 256
0x29   = 41
0x130 = 304

And it only sees numbers in the range 0-100 (decimal). Consider it using 
speed = input % 100.
Then you'll see that 0x66 (102dec) = 2%, 0x100(256) = ~56%, 0x130(304) is 4%

With the exception of 0x29 which is 97%. You sure that isn't a typo?
If it is, then all we have to do (assuming that bit 7 being 1 or 0 is harmless) is write an automated control script to run in the background et voila!

EDIT:
One more thing, for the control script.
What does GFSD return after each SFSD?
If it returns exactly what you put in SFSD (assuming 0-99 decimal input speed) it would make the scripting a lot easier and cleaner.

---

### Post by idodos on 2014-04-19
Oh, alright, didn't know you could just throw decimal numbers at it lol
And yeah it was a typo, I've meant 0x129

Seems to be a little issue with the script, setting SFSD to 20 returns a value of 19% in the script.
While GFSD returns 0x14 which is 20, other than that it works well, 0-100 and all.

Edit:
Yes GFSD returns exactly what is put in SFSD.

I don't know if bit 7 is harmless, it just never seems to go to "0". Perhaps if I set fan speed to 101.. lol

---

### Post by chris-c on 2014-04-19
Ok. Here's the control script I use, slightly modified for your control methods.
It's not the one we'll be running in the background, but should be good for testing the final thing.
```
#!/bin/bash
# 
# HP ProBook 4320s Fan Control
# DEBUG Script + Interface
# V 0.0.1
# ACPI SFSD/GFSD Methods


INTERV=5 # Polling interval, seconds
HYST=5   # Hysterisis (deg. C)
TSTEP=( 55 60 70 80 90 ) # Temperature Steps (deg. C)
SSTEP=( 00 14 28 3c 64 ) # Speed Steps (Fan speed percentage, hexadecimal, 00 < x < 64)


# Make sure only root can run our script
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi


# Make sure acpi_call is installed
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi


if [ ${#SSTEP[@]} -ne ${#SSTEP[@]} ]; then
    echo "Error: Speed Step length and Temp Step length not equal!"
    exit
fi


acpi_call () {
    echo "$*" > /proc/acpi/call
    echo "$(cat /proc/acpi/call)"
}


get_speed () {
    CMD="\_SB.PCI0.LPCB.EC0.GFSD"
    echo "$(acpi_call $CMD)"
}


set_speed () {
    CMD="\_SB.PCI0.LPCB.EC0.SFSD 0x$1"
    echo "$(acpi_call $CMD)"
}


display () {
    # Display the magic
    echo -en "\ec"
    echo -en "ProBook 4320s Fan Control Interface.\nUse at your own risk!\n\n"
    echo -e  "   Temperature: $TEMP\xC2\xB0C"
    echo -e  "  Current Step: $STEP"
    echo -e  "      Set Step: $NSTEP"
    echo -e  " Current Speed: $(( $(echo "obase=10; ibase=16; ${CURSPD^^}" | bc ) % 100 ))%"
}


# Sizing and Titling
# echo -en "\033[8;5;20t"
echo -en "\033]0;ProBook Fan Control DEBUG Script\007"


while true; do
    # Get CPU temperature
    SENSE="$(sensors)"
    CORE0=$(echo "$SENSE"|grep 'Core 0'|awk '{print $3}'|cut -b2,3)
    #CORE2=$(echo "$SENSE"|grep 'Core 2'|awk '{print $3}'|cut -b2,3)
    #SUM="`expr $CORE0 + $CORE2`"
    #TEMP="`expr $SUM / 2`"
    TEMP=$CORE0


    # Calculate the current speed step
    CURSPD=$(get_speed|cut -b3,4)
    # echo $CURSPD
    # exit


    STEP=-1
    for (( i = 0; i < ${#SSTEP[@]}; i++ )); do
       if [ "${SSTEP[$i]}" = "$CURSPD" ]; then
           STEP=$i;
       fi
    done


    # Make the magic happen


    NSTEP="-"
    if [ $STEP -eq -1 ]; then
        #echo "Error: Speed $(get_speed) not in dictionary. uh-oh!"
        STEP=0 # If we didn't set the speed, assume the fan is off and start over.
        # exit
    else
        if [ $TEMP -gt ${TSTEP[$STEP+1]} ]; then
            if [ `expr $STEP + 1` -eq ${#SSTEP[@]} ]; then
                sleep $INTERV
                continue # Sky High Step
            fi
            # Step Up
            set_speed "${SSTEP[$STEP+1]}" > /dev/null
            NSTEP=`expr $STEP + 1`
            # echo -e "Stepping up to: `expr $STEP + 1`; Temp: $TEMP\xC2\xB0C"
        elif [ $TEMP -lt `expr ${TSTEP[$STEP]} - $HYST` ]; then
            if [ $STEP -eq 0 ]; then
                sleep $INTERV
                continue # Rock Bottom Step
            fi
            # Step Down
            set_speed "${SSTEP[$STEP-1]}" > /dev/null
            # echo -e "Stepping down to: `expr $STEP - 1`; Temp: $TEMP\xC2\xB0C"
            NSTEP=`expr $STEP - 1`
        fi
    fi
    display
    sleep $INTERV
done
```

Put it in a file, run it in a terminal and put the laptop through its paces.
It should control the fan automatically as long as the terminal is running.
Temperature is the temp. of Core 0,
Current Step is one of 5, see the first lines of the script and
Next Step should display something other than "-" only when 'switching gears' on the fan
And in the code, Hysteresis is the number of deg. C the temperature should drop before lowering the speed step. Otherwise, when the temperature fluctuates at near for example 69~71 (between steps 2 and 3) the fan would be constantly switching speeds.

I couldn't test it on my machine, so put it through its paces and tell me if anything goes wrong.

EDIT:
Typo in the script, should say "sleep $INTERV" not "leep .." in the main loop.

---

### Post by idodos on 2014-04-19
For some reason I am unable to execute the script:
```
sudo: unable to execute ./pb_control: No such file or directory

```

Any ideas?

Edit: Saw your edit, nvm lol
Edit 2: Still wont execute.

---

### Post by chris-c on 2014-04-19
That means you're not in the directory where you saved your file. "./" means current directory.
Either that, or you have a typo in your name. Either an extension, or uppercase characters, etc.

BTW, I've edited the script yet again, be sure to copy it again before you execute it.

---

### Post by idodos on 2014-04-19
Nope, in the same folder, I've used "tab" to auto complete it.
It is set as an executable.
It's right next to pb_debug which does execute. It simply wont execute.

---

### Post by chris-c on 2014-04-19
What the proverb?
Well, something must have happened when copy-pasting here. See if the script has an extra "#" after #!/bin/bash, if so remove it and try again.

---

### Post by idodos on 2014-04-19
It's not really doing anything, the fan was set to 30% initially and it read it as 31%
The "Current Step" is always set to "0"
"Set Step" is always "-"
I'm stressing the cpu using "Stress"
It's currently idling at 77-78 celsius

The Control interface just crashed with the following error:
```
./pb_control: line 59: % 100 : syntax error: operand expected (error token is "% 100 ")

```

Maybe just as it was hitting 79 celsius

---

### Post by chris-c on 2014-04-19
```
#!/bin/bash
# 
# HP ProBook 4320s Fan Control
# DEBUG Script + Interface
# V 0.0.1
# ACPI SFSD/GFSD Methods


INTERV=5 # Polling interval, seconds
HYST=5   # Hysterisis (deg. C)
TSTEP=( 55 60 70 80 90 ) # Temperature Steps (deg. C)
SSTEP=( 00 14 28 3c 64 ) # Speed Steps (Fan speed percentage, hexadecimal, 00 < x < 64)


# Make sure only root can run our script
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi


# Make sure acpi_call is installed
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi


if [ ${#SSTEP[@]} -ne ${#SSTEP[@]} ]; then
    echo "Error: Speed Step length and Temp Step length not equal!"
    exit
fi


acpi_call () {
    echo "$*" > /proc/acpi/call
    echo "$(cat /proc/acpi/call)"
}


get_speed () {
    CMD="\_SB.PCI0.LPCB.EC0.GFSD"
    echo "$(acpi_call $CMD)"
}


set_speed () {
    CMD="\_SB.PCI0.LPCB.EC0.SFSD 0x$1"
    echo "$(acpi_call $CMD)"
}


display () {
    # Display the magic
    echo -en "\ec"
    echo -en "ProBook 4320s Fan Control Interface.\nUse at your own risk!\n\n"
    echo -e  "   Temperature: $TEMP\xC2\xB0C"
    echo -e  "  Current Step: $STEP"
    echo -e  "      Set Step: $NSTEP"
    echo -e  "  Target Speed: $(( $(echo "obase=10; ibase=16; ${SSTEP[$i]^^}" | bc ) ))%"
    echo -e  "Reported Speed: $(echo "obase=10; ibase=16; ${CURSPD^^}" | bc )%"
}


# Sizing and Titling
# echo -en "\033[8;5;20t"
echo -en "\033]0;ProBook Fan Control DEBUG Script\007"


while true; do
    # Get CPU temperature
    SENSE="$(sensors)"
    CORE0=$(echo "$SENSE"|grep 'Core 0'|awk '{print $3}'|cut -b2,3)
    #CORE2=$(echo "$SENSE"|grep 'Core 2'|awk '{print $3}'|cut -b2,3)
    #SUM="`expr $CORE0 + $CORE2`"
    #TEMP="`expr $SUM / 2`"
    TEMP=$CORE0


    # Calculate the current speed step
    CURSPD=$(get_speed|cut -b3,4)
    # echo $CURSPD
    # exit


    STEP=-1
    for (( i = 0; i < ${#SSTEP[@]}; i++ )); do
        ST=$(echo "obase=10; ibase=16; ${SSTEP[$i]^^}" | bc )
        CS=$(echo "obase=10; ibase=16; ${CURSPD^^}" | bc )
        # Allow for 2% deviation from target speed
       if [ "$(( $ST + 1 ))" -ge "$CS" ] && [ "$(( $ST - 1 ))" -le "$CS" ]; then
           STEP=$i;
       fi
    done


    # Make the magic happen


    NSTEP="-"
    if [ $STEP -eq -1 ]; then
        echo "Error: Speed $(get_speed) not in dictionary. uh-oh!"
        # STEP=0 # If we didn't set the speed, assume the fan is off and start over.
        exit
    else
        if [ $TEMP -gt ${TSTEP[$STEP+1]} ]; then
            if [ `expr $STEP + 1` -eq ${#SSTEP[@]} ]; then
                sleep $INTERV
                continue # Sky High Step
            fi
            # Step Up
            set_speed "${SSTEP[$STEP+1]}" > /dev/null
            NSTEP=`expr $STEP + 1`
            # echo -e "Stepping up to: `expr $STEP + 1`; Temp: $TEMP\xC2\xB0C"
        elif [ $TEMP -lt `expr ${TSTEP[$STEP]} - $HYST` ]; then
            if [ $STEP -eq 0 ]; then
                sleep $INTERV
                continue # Rock Bottom Step
            fi
            # Step Down
            set_speed "${SSTEP[$STEP-1]}" > /dev/null
            # echo -e "Stepping down to: `expr $STEP - 1`; Temp: $TEMP\xC2\xB0C"
            NSTEP=`expr $STEP - 1`
        fi
    fi
    display
    sleep $INTERV
done
```

Try this. Hopefully, less bugs. :D

The script this is based on is actually my very first bash script, and I'm still learning as I go, so things may not be perfect.
Maybe if this doesn't work, (the methods to set fan speed are OK, we know how to call them manually), you could ask somebody with more experience in automating commands?

Fingers Crossed!

EDIT: Again that # at the end of the first line... What's wrong with this forum's editor?

---

### Post by idodos on 2014-04-19
```
Error: Speed 0x1f not in dictionary. uh-oh!

```

Uh-oh?

---

### Post by chris-c on 2014-04-19
Dang it man! Not on the last leg of the race!

I'm assuming you set the speed at 30%... calling GFSD from within this script returns 31%, when you said that directly it returned bang-on 30. What's happening?

And about it not being in the dictionary, it means that 30 isn't one of the 5 speed steps we set up at the beginning. It's a logic error on my part, one that I don't know how to fix off the top of my head.

Turn this:
```

# Make the magic happen    

NSTEP="-"
    if [ $STEP -eq -1 ]; then
        echo "Error: Speed $(get_speed) not in dictionary. uh-oh!"
        # STEP=0 # If we didn't set the speed, assume the fan is off and start over.
        exit

```
into this:
```

# Make the magic happen


    NSTEP="-"
    if [ $STEP -eq -1 ]; then
        #echo "Error: Speed $(get_speed) not in dictionary. uh-oh!"
         STEP=0 # If we didn't set the speed, assume the fan is off and start over.
        #exit

```

While I go and set up another topic on how to make this script work. I'll edit this post when I have it up in the programming department.

---

### Post by idodos on 2014-04-19
```
ProBook 4320s Fan Control Interface.
Use at your own risk!

   Temperature: 43°C
  Current Step: 0
      Set Step: -
  Target Speed: 0%
Reported Speed: 31%


```

This doesn't seem right, it again doesn't do anything. I think.

And it is odd that GFSD has a slightly different report in your script.

Edit: Your debug script is spot on though.

---

### Post by chris-c on 2014-04-19
Waaaaait... :)
Did you set that 30% from MFAC?

Keep the script open, open up another root prompt and
1. do MFAC 0 0
2. do SFSD 30, see if reported speed goes to 30%
3. do SFSD 0, if current step stays on 0 (right now, 43 deg. C is well below the 55 we set for the first speed stop), if step goes up, script's working!
4. do another stress test, as far as I can tell, this should be working.

---

### Post by idodos on 2014-04-19
No I've used SFSD.
Also, if you set the speed using MFAC, GFSD doesn't know that the fan is even working.
But I've been using SFSD since the first time you told me to check if it works.
Although, as far as I can tell, they do the exact same thing only in different ways.

But I'm stressing again anyways.
Why is the "target speed" 0?

Edit:
```
   Temperature: 84°C
  Current Step: 0
      Set Step: -
  Target Speed: 0%
Reported Speed: 31%



```
Nope.. :(

---

### Post by chris-c on 2014-04-19
```

#!/bin/bash
# 
# HP ProBook 4320s Fan Control
# DEBUG Script + Interface
# V 0.0.1
# ACPI SFSD/GFSD Methods


INTERV=1 # Polling interval, seconds
HYST=5   # Hysterisis (deg. C)
TSTEP=( 55 60 70 80 90 ) # Temperature Steps (deg. C)
SSTEP=( 00 14 28 3c 64 ) # Speed Steps (Fan speed percentage, hexadecimal, 00 < x < 64)


# Make sure only root can run our script
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi


# Make sure acpi_call is installed
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi


if [ ${#SSTEP[@]} -ne ${#TSTEP[@]} ]; then
    echo "Error: Speed Step length and Temp Step length not equal!"
    exit
fi


acpi_call () {
    echo "$*" > /proc/acpi/call
    echo "$(cat /proc/acpi/call)"
}


get_speed () {
    # Exact speed
    PWM0h=$(acpi_call "\_SB.PCI0.LPCB.EC0.PWM0"|cut -b3,4)
    PWM0d=$(echo "obase=10; ibase=16; ${PWM0h^^}" | bc )
    SPD=$((($PWM0d & 127) >> 1))
    echo $(( 100 - ($SPD*100)/64 ))
    # echo "30"
}


set_speed () {
    CMD="\_SB.PCI0.LPCB.EC0.SFSD 0x$1"
    echo "$(acpi_call $CMD)"
}


display () {
    # Display the magic
    echo -en "\ec"
    echo -en "ProBook 4320s Fan Control Interface.\nUse at your own risk!\n\n"
    echo -e  "   Temperature: $TEMP\xC2\xB0C"
    echo -e  "  Current Step: $STEP"
    echo -e  "      Set Step: $NSTEP"
    echo -e  "  Target Speed: $(( $(echo "obase=10; ibase=16; ${SSTEP[$i]^^}" | bc ) ))%"
    echo -e  "Reported Speed: $CURSPD%"
}


# Sizing and Titling
# echo -en "\033[8;5;20t"
echo -en "\033]0;ProBook Fan Control DEBUG Script\007"


while true; do
    # Get CPU temperature
    SENSE="$(sensors)"
    CORE0=$(echo "$SENSE"|grep 'Core 0'|awk '{print $3}'|cut -b2,3)
    #CORE2=$(echo "$SENSE"|grep 'Core 2'|awk '{print $3}'|cut -b2,3)
    #SUM="`expr $CORE0 + $CORE2`"
    #TEMP="`expr $SUM / 2`"
    TEMP=$CORE0


    # Calculate the current speed step
    CURSPD=$(get_speed)
     # echo $CURSPD
     # exit


    STEP=-1
    for (( i = 0; i < ${#SSTEP[@]}; i++ )); do
        ST=$(echo "obase=10; ibase=16; ${SSTEP[$i]^^}" | bc )
        CS=$CURSPD
        # Allow for 2% deviation from target speed
       if [ "$(( $ST + 1 ))" -ge "$CS" ] && [ "$(( $ST - 1 ))" -le "$CS" ]; then
           STEP=$i;
       fi
    done


    # Make the magic happen


    NSTEP="-"
    if [ $STEP -eq -1 ]; then
        #echo "Error: Speed $(get_speed) not in dictionary. uh-oh!"
         #STEP=0 # If we didn't set the speed, assume the fan is off and start over.
         NSTEP=0
         set_speed "0"
         display
         continue
        #exit
    else
        if [ $TEMP -gt ${TSTEP[$STEP+1]} ]; then
            if [ `expr $STEP + 1` -eq ${#SSTEP[@]} ]; then
                sleep $INTERV
                continue # Sky High Step
            fi
            # Step Up
            set_speed "${SSTEP[$STEP+1]}" > /dev/null
            NSTEP=`expr $STEP + 1`
            # echo -e "Stepping up to: `expr $STEP + 1`; Temp: $TEMP\xC2\xB0C"
        elif [ $TEMP -lt `expr ${TSTEP[$STEP]} - $HYST` ]; then
            if [ $STEP -eq 0 ]; then
                sleep $INTERV
                continue # Rock Bottom Step
            fi
            # Step Down
            set_speed "${SSTEP[$STEP-1]}" > /dev/null
            # echo -e "Stepping down to: `expr $STEP - 1`; Temp: $TEMP\xC2\xB0C"
            NSTEP=`expr $STEP - 1`
        fi
    fi
    display
    sleep $INTERV
done

```
Possibly?
I'm running out of ideas! :(

---

### Post by idodos on 2014-04-19
It's doing something!
But not as intended.

It's a loop
100% 60% 40% 19%

I feel like it's actually 20% and 19% is reported.
Anyways it's an endless loop.

```
   Temperature: 36°C
  Current Step: 4
      Set Step: 3
  Target Speed: 0%
Reported Speed: 100%

```

```
   Temperature: 37°C
  Current Step: 3
      Set Step: 2
  Target Speed: 0%
Reported Speed: 60%
```

```
   Temperature: 37°C
  Current Step: 2
      Set Step: 1
  Target Speed: 0%
Reported Speed: 40%

```

```
   Temperature: 38°C
  Current Step: 1
      Set Step: 0
  Target Speed: 0%
Reported Speed: 19%

```

---

### Post by chris-c on 2014-04-19
Ok, that should be a quick fix...
Replace
```

get_speed () {
    # Exact speed
    PWM0h=$(acpi_call "\_SB.PCI0.LPCB.EC0.PWM0"|cut -b3,4)
    PWM0d=$(echo "obase=10; ibase=16; ${PWM0h^^}" | bc )
    SPD=$((($PWM0d & 127) >> 1))
    echo $(( 100 - ($SPD*100)/64 ))
    # echo "30"
}

```
with
```

get_speed () {
    # Exact speed
    local PWM0h=$(acpi_call "\_SB.PCI0.LPCB.EC0.PWM0"|cut -b3,4)
    local PWM0d=$(echo "obase=10; ibase=16; ${PWM0h^^}" | bc )
    local FANOFF=$(($PWM0d & 1))
    if [ $FANOFF -eq 1 ]; then
        echo "0"
    else
        local SPD=$((($PWM0d & 127) >> 1))
        echo $(( 100 - ($SPD*100)/64 ))
    fi
}

```

---

### Post by idodos on 2014-04-19
Working perfectly!

Why did you set it to be 0% below 55c?
That's weird. lol

Also, Core 2 seems to be a little hotter (2 Celsius or so), so I'd think using that temp would be better.


Awesome though :D

---

### Post by chris-c on 2014-04-19
Finally! Phew!

> [COLOR=#000000]Why did you set it to be 0% below 55c?[/COLOR]
On my laptop the fan would be constantly running otherwise. 55 is acceptable, seeing that the battery and hard drive are well within spec at that temp.

You may change the steps as you see fit, now. It's your laptop, after all.
And about the Core 2, yeah, I wasn't sure how many cores you had.

By replacing
```

# Get CPU temperature
SENSE="$(sensors)"
CORE0=$(echo "$SENSE"|grep 'Core 0'|awk '{print $3}'|cut -b2,3)
#CORE2=$(echo "$SENSE"|grep 'Core 2'|awk '{print $3}'|cut -b2,3)
#SUM="`expr $CORE0 + $CORE2`"
#TEMP="`expr $SUM / 2`"
TEMP=$CORE0

```
with
```

# Get CPU temperature
SENSE="$(sensors)"
CORE0=$(echo "$SENSE"|grep 'Core 0'|awk '{print $3}'|cut -b2,3)
CORE2=$(echo "$SENSE"|grep 'Core 2'|awk '{print $3}'|cut -b2,3)
SUM="`expr $CORE0 + $CORE2`"
TEMP="`expr $SUM / 2`"
#TEMP=$CORE0

```
You should get an average between the cores as you temperature for calculations.

With that out of the way, It's only disabling the display bits and making it run on boot and you're set.
Editing my comment in ~1 minute.

EDIT:
So... took longer than I expected.
```

#!/bin/bash
# 
# HP ProBook 4320s Fan Control Script
# V 0.1.0
# ACPI SFSD/GFSD Methods
# ASSUMING DUAL CORE CPU
# For single core CPU check comments below


INTERV=1 # Polling interval, seconds
HYST=5   # Hysterisis (deg. C)
TSTEP=( 55 60 70 80 90 128 ) # Temperature Steps (deg. C)
SSTEP=( 00 14 28 3c 64 64  ) # Speed Steps (Fan speed percentage, hexadecimal, 00 < x < 64)
# FIRST speed step must always be 00
# LAST temperature step must always be 128
# You may add as many steps in between, as long the number of temperature and speed steps are equal




# --- NO EDITING BEYOND HERE NECESSARY ---


# Make sure only root can run our script
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi


# Make sure acpi_call is installed
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi


if [ ${#SSTEP[@]} -ne ${#TSTEP[@]} ]; then
    echo "Error: Speed Step length and Temp Step length not equal!"
    exit
fi


acpi_call () {
    echo "$*" > /proc/acpi/call
    echo "$(cat /proc/acpi/call)"
}


get_speed () {
    # Exact speed
    local PWM0h=$(acpi_call "\_SB.PCI0.LPCB.EC0.PWM0"|cut -b3,4)
    local PWM0d=$(echo "obase=10; ibase=16; ${PWM0h^^}" | bc )
    local FANOFF=$(($PWM0d & 1))
    if [ $FANOFF -eq 1 ]; then
        echo "0"
    else
        local SPD=$((($PWM0d & 127) >> 1))
        echo $(( 100 - ($SPD*100)/64 ))
    fi
}


set_speed () {
    CMD="\_SB.PCI0.LPCB.EC0.SFSD 0x$1"
    echo "$(acpi_call $CMD)"
}


# display () {
#  # Display the magic
#  echo -en "\ec"
#  echo -en "ProBook 4320s Fan Control Interface.\nUse at your own risk!\n\n"
#  echo -e  "   Temperature: $TEMP\xC2\xB0C"
#  echo -e  "  Current Step: $STEP"
#  echo -e  "      Set Step: $NSTEP"
#  echo -e  "  Target Speed: $(( $(echo "obase=10; ibase=16; ${SSTEP[$i]^^}" | bc ) ))%"
#  echo -e  "Reported Speed: $CURSPD%"
# }


# Sizing and Titling
# echo -en "\033[8;5;20t"
# echo -en "\033]0;ProBook Fan Control DEBUG Script\007"


while true; do
    # Get CPU temperature
    SENSE="$(sensors)"
    CORE0=$(echo "$SENSE"|grep 'Core 0'|awk '{print $3}'|cut -b2,3)
    # FOR SINGLE CORE CPU
    # Comment from here
    CORE2=$(echo "$SENSE"|grep 'Core 2'|awk '{print $3}'|cut -b2,3)
    SUM="`expr $CORE0 + $CORE2`"
    TEMP=`expr $SUM / 2`
    #UNTIL HERE and uncomment the line below
    #TEMP=$CORE0


    # Calculate the current speed step
    CURSPD=$(get_speed)


    STEP=-1
    for (( i = 0; i < ${#SSTEP[@]}; i++ )); do
        ST=$(echo "obase=10; ibase=16; ${SSTEP[$i]^^}" | bc )
        CS=$CURSPD
        # Allow for 2% deviation from target speed
       if [ "$(( $ST + 1 ))" -ge "$CS" ] && [ "$(( $ST - 1 ))" -le "$CS" ]; then
           STEP=$i;
           break
       fi
    done


    # Make the magic happen


    NSTEP="-"
    if [ $STEP -eq -1 ]; then
        # If we didn't set the speed, turn the fan off and start over.
        NSTEP=0
        STEP=0
        set_speed "0"
         #display
        continue
    else
        echo $TEMP
        if [ $TEMP -gt ${TSTEP[$STEP+1]} ]; then
            if [ `expr $STEP + 1` -eq ${#SSTEP[@]} ]; then
                sleep $INTERV
                continue # Sky High Step
            fi
            # Step Up
            set_speed "${SSTEP[$STEP+1]}" > /dev/null
            NSTEP=`expr $STEP + 1`
            # echo -e "Stepping up to: `expr $STEP + 1`; Temp: $TEMP\xC2\xB0C"
        elif [ $TEMP -lt `expr ${TSTEP[$STEP]} - $HYST` ]; then
            if [ $STEP -eq 0 ]; then
                sleep $INTERV
                continue # Rock Bottom Step
            fi
            # Step Down
            set_speed "${SSTEP[$STEP-1]}" > /dev/null
            # echo -e "Stepping down to: `expr $STEP - 1`; Temp: $TEMP\xC2\xB0C"
            NSTEP=`expr $STEP - 1`
        fi
    fi
     #display
    sleep $INTERV
done

```

Put this in a file with a descriptive name, like pb_fan, set its executable bit, copy it somewhere in your $PATH (I put mine in /sbin).
make sure you can run the script without specifying its path
```

pb_fan

```
now create a log file for it:
```

touch /var/log/pb_fan.log

```
and now edit /etc/rc.local and add this line before exit 0:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
**$(nohup pb_fan 0<&- &>/var/log/pb_fan.log &) &**
exit 0

```

Restart and you're done!

Whenever you want to change any of the values, edit the file from your $PATH (e.g. /sbin/pb_fan), change the values, and restart.

---

### Post by idodos on 2014-04-19
Solved, thanks a lot, awesome work! : )

Hopefully this will help others with similar issues!

---

### Post by exit4 on 2014-04-20
[COLOR=#000000]thanks, works for me on HP Compaq 6730s[/COLOR]

---

### Post by exit4 on 2014-04-20
sorry,  last script not work 
> 
/sbin/pb_fan: line 129: [: -gt: unary operator expected
/sbin/pb_fan: line 138: [: -lt: unary operator expected
expr: syntax error
expr: syntax error


edit script "CORE2 >> CORE1" !!!

thank)

---

### Post by aaronblankenship on 2014-04-26
Forgive me for barging in, but I'm having a similar issue with a ProBook 4410t.  Fixing the fan on Ub 12 wasn't quite as involved, this is a bit complex although I think it will solve my issue.  Are there any chances something will be released as a 14 LTS patch?

---

### Post by tolyan2 on 2014-04-27
Hi!
I run this script on HP 4740s, ans see:

ProBook 4320s Fan Control Interface.
Use at your own risk!

   Temperature: 38°C
  Current Step: 4
      Set Step: 3
  Target Speed: 0%
Reported Speed: 100%

speed of fan is not change. What can I do for fix this? Thanks!

---

### Post by tolyan2 on 2014-04-27
Upd: I rebuild acpi_call, and try: 
root@tolyan-hp:/home/tln# echo "\_SB.PCI0.LPCB.EC0.KRFS" > /proc/acpi/call && echo $(cat /proc/acpi/call)
0xffalled
root@tolyan-hp:/home/tln# echo "\_SB.PCI0.LPCB.EC0.KSFS 50" > /proc/acpi/call && echo $(cat /proc/acpi/call)
0x32alled


Why it not working?

---

### Post by tolyan2 on 2014-04-27
echo "\_SB.PCI0.LPCB.EC0.KFCL 0 100" > /proc/acpi/call && echo $(cat /proc/acpi/call) 
this command make fan very fast

echo "\_SB.PCI0.LPCB.EC0.KFCL 0 00" > /proc/acpi/call && echo $(cat /proc/acpi/call)
this - slow, but not very slow. audible noise. How make fan more slowly?

---

### Post by vroyibg on 2014-04-30
Same proplem with my new hp probook 450 laptop. 
Can i use this solution ?
Thanks.

---

