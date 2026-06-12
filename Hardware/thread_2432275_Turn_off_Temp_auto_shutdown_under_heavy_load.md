---
title: "Turn off Temp auto shutdown under heavy load"
date: 2019-11-29
forum: Hardware
---

### Post by exonlive on 2019-11-29
I am using a slightly older laptop with a hybrid config AMD A10 with 8750G GPU. I've had a variety of issues with this config across many OS' but can usually find a way around it.

I believe it has a damaged or poorly configured temperature monitor as I have had this issue carry across from Windows 10 (however on Win10 or 8 I can fairly easily work around it).

Using sensors-detect I am getting:

radeon-pci-0100
Adapter: PCI adapter
temp1:            N/A  (crit = +120.0°C, hyst = +90.0°C)

asus-isa-0000
Adapter: ISA adapter
cpu_fan:     2500 RPM
temp1:       +6280.0°C  

radeon-pci-0008
Adapter: PCI adapter
temp1:        +42.0°C  (crit = +120.0°C, hyst = +90.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +42.2°C  (high = +70.0°C)
                       (crit = +97.0°C, hyst = +96.0°C)

Now obviously it is not actually 6280 degrees celcius as that would be hotter than our sun :)

This laptop only needs to run another month or two while I wait on my new hardware to arrive for my new build so I am not looking to make hardware changes for it, but I have put fresh thermal compound and cleaned dust from vents and fans.

Is there a way I can turn off the auto shutdown of the CPU based on temp? I know its not overheating. It is cool to the touch when it does a hard shut down during a video, or under heavy loads.

Thanks in advance

Edit: I suppose I also am wondering why it would turn on at all at this temperature and why it only does a hard shut down under heavy load?



Sensor info if any use? (Linux beginner)

Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

---

### Post by Irihapeti on 2019-11-29
Thread moved to ***Hardware***.

---

