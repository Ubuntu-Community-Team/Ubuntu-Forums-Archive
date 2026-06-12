---
title: "Java at 100% CPU usage and high temperatures."
date: 2013-04-19
forum: Hardware
---

### Post by x1gma on 2013-04-19
Hello ubuntuforums-users,

I have the following problem on my ThinkPad X230. I installed Ubuntu a few days ago, and my X230 had higher temperatures then on Win7 before, even when not performing huge tasks.
 I tried to pinpoint the problem as much as I could, and thought at first that its a problem with the fan control, that it might have been better in the ThinkPad software on windows, than in the thinkpad_acpi. 
Also I looked up the BIOS settings regarding the automatical down-clocking in battery mode and power saving options that might affect the fan, but everything was fine.
Today I think I found my problem. When running something Java related, Java is taking constantly 99-100% CPU. I already updated from openjdk-6 to openjdk-7 and have openjdk now completely replaced by oracle-java - no change.

I am reading the temperatures with lm-sensors (sensors-detect was done), CPU usage with "top".
On windows even running Xilinx ISE didnt made the temperatures higher then 60-70°, now when having my X230 in AC mode (full clocks) idling in Eclipse makes my CPU go to 75°-80°. I know these temperatures are not critical, but I really dont think that running it with constant 70°+ is good for the hardware either.

My X230 configuration:
Intel Core i5-3320M 2.60 GHz (max. 3.3 Ghz Intel Turbo Boost)
8GB RAM
Samsung 840 128GB
Intel 4000HD GPU

3.5.0-27-generic x86_64
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
sudo lshw -html output: [http://www.file-upload.net/download-7487425/System.html.html](http://www.file-upload.net/download-7487425/System.html.html)

Please tell me if you need any other information.

I also heard about thinkfan, but to be honest I do not really want to manually configurate it, because I do not want to make things worse. If anyone has a configuration for thinkfan I would appreciate it.

Did anyone experience a similar problem, or knows a way how to troubleshoot it?

Edit: Just tried it again. Idle, 45°. Starting Eclipse, still at 45°, Java at 0% CPU. Ran one of my current JUnit tests, boom, skyrocket to 70°, Java stuck at 100%, even after stopping everything, remaining battery time halved.

Thanks in advance,
x1gma

---

