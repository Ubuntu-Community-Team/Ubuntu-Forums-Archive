---
title: "Ubuntu 14.04 - What's the best way to reduce laptop temperature?"
date: 2014-05-26
forum: Hardware
---

### Post by socheon on 2014-05-26
Hi. I just installed Ubuntu 14.04 on my Samsung Series 7 laptop.

I installed the "Hardware Sensors Indicator" tool to check my laptop's temperature. The CPU temperature on my computer is around 78 celcius.

What's the best way to lower this temperature? What is the most popular tool?

Thanks.

---

### Post by TheFu on 2014-05-26
Clean the dust from everywhere
Keep the fan exhaust free from obstructions
Use lower power HDDs
Check that the CPU fan is working
Check that the CPU heat-pipe is connecting properly

There may be a way to lower the CPU speed - I don't know anything about that. Sorry.

---

### Post by WinEunuchs2Unix on 2014-05-26
I did a quick check and your limited model number information shows Intel Core 7 running at 2.3 GHz.  On my Intel Core 2 I had to slow it from 2 GHz to 1 GHz which is done in the BIOS upon boot by pressing F2 (for the Toshiba I have).  The temp drops to about 60c instead of over 85c which shuts the machine right off.  Also in Chrome's Flash Player plug in I downloaded the latest Intel Video Driver which runs the GPU (Graphic Processing Unit) and told Google not to run Flash Player off the CPU (which was causing it to run at 100%) and use the GPU for graphics like Flash Player (videos for TV and Youtube) which reduced the CPU to 50% or so.

There is a package called "P-Sensor" you can download through the little Ubuntu brief case with an "A" on it (for Apps?) that will show your CPU% along with the temp of your motherboard, Core 0 and Core 1 (for a dual core CPU).  I believe your newer laptop will have even more indicators in P-Sensor like fan speed because it might use Intel's "P-State" flags/variables.

Hope this leads you on the right path (be prepared to devote a few quite hours of research :D)).

---

### Post by mastablasta on 2014-05-27
latest GPU drivers, cleaning exhausts and fan.

check TLP for power management or check the default power manager to see if it is managing CPU porpperly. 
check for processes consuming the CPU. CPU should scale down when not in use. as it reduces in activity it also reduces in temerature.

---

### Post by socheon on 2014-05-27
Thanks [**[COLOR=#000000]WinEunuchs2Unix[/COLOR]**]("http://ubuntuforums.org/member.php?u=1925810"). As suggested, I installed P-Sensor. The temperature at idle state is rather high around 78 Celcius. I can rule out Flash Player as the culprit.
With default settings, playing YouTube videos only uses 12% of my CPU although the temperature increased to 87-91 Celcius. P-Sensor is showing 4 cores. By the way, what are the acpitz readings which are labelled as "temp1" and "temp2"?

Hi [**[COLOR=#000000]mastablasta[/COLOR]**]("http://ubuntuforums.org/member.php?u=964486"). Thanks for the suggestion. I installed TLP.

sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw
sudo tlp startAt idle, the temperature is still showing 80 Celcius. I will spend more time configuring it and see whether can bring it down.

How do I find the default power manager? All Settings > Power only allows me to configure when to suspend the computer.

Any other tools can you recommend? [https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower) has several options but not sure whether they will conflict with each other since they are all trying to achieve the same thing.

I know on Windows I can choose to scale down the CPU and that helped with reducing the temperature significantly.

I will try removing the dust too but hopefully it would not be too hard to disassemble Samsung Series 7 laptop.

---

### Post by WinEunuchs2Unix on 2014-05-27
There's actually a very heated discussion (pun intended) about ACPI control of fans between Kernel version 3.12 and Kernel  3.13 (which Ubuntu 14.04) uses.  It applies up to Kernel version 3.15 (a beta thingy??) as well.  Anyway at the end of the thread (down around comment 34?) you'll find a link to patch #4124871 which contains a diff file to subtract old C code and add new C code into the source files for a recompile.  I haven't tried this myself yet but will try to remember to post back after I do.  I'm still working on a new driver gm965temp (written by the same author as the patch) which should allow me to show the temperature of the Intel GME965 Family Express Chipset and ICH8 Controller (basically speaking).

In the mean time I'm pretending my warm palms are because I'm in the Bahamas and not because mobo (motherboard) temp is 60c.

Oh yes in a nutshell under Kernel 3.12 would run fans 30% speed but under Kernel 3.13 a bug caused 0% speed until critical temp and then it would hit 90%.  Then fan would shut off again instead of a normal 30% "idling" speed.  I apologize if tonight's research is too technical for this section or I revealed too much information.

---

### Post by WinEunuchs2Unix on 2014-05-27
Hi [COLOR=#000000][[COLOR=#000000]socheon[/COLOR]]("http://ubuntuforums.org/member.php?u=1925619") [/COLOR]
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG][COLOR=#000000][INDENT]
"  What are the acpitz readings which are labelled as "temp1" and "temp2"?[COLOR=#222222]"[/COLOR][/INDENT]


[/COLOR]
My P-Sensors only shows a "temp1" which I believe comes from the motherboard aka "mobo".  I guess your temp2 might come from the battery or FSB (front system board) or something like that.  I've only got a few days under my belt in this arena and cannot be much help on that particular subject.  Can you check with the P-Sensor author's website and see if he gives a table of temp#'s and how they correspond to Intel chip sets?

As far as YouTube I don't really go to that site often and was recalling from my own faulty memory that it uses Adobe Flash Player for videos and perhaps it does not. The gist of utlizing the GPU (Graphical Processing Unit) which sits next to the CPU (Central Processing Unit) to reduce CPU heat still holds true in any case.  The GPU is optimized for floating point arithmetic (or something like that) which means it can handle video processing more efficiently than the CPU.  Sorry I was a failure at art and my knowledge of CPU's and GPU's is 10 years stale (took time off for a war or two) so can't elaborate much better :(

---

### Post by WinEunuchs2Unix on 2014-05-31
A status update related to this issue.  I installed "Flash Control" plug in for google chrome that hides all things flash player related which speeds up web page processing and stops sound blaring adds and visually distracting advertising videos from playing.  Then you white-list sites where you actually do want to watch the news / videos.  You can on-demand watch a given advertisement embedded in a web site's frame.

---

