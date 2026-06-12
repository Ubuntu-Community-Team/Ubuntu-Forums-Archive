---
title: "Dell Studio 1557 overheating issue"
date: 2010-08-15
forum: Hardware
---

### Post by Hemenesgard on 2010-08-15
Hi guys, i am having the following problem.
I installed Ubuntu 10.04 (64bits) on my laptop in dual boot with Windows 7, and now it is overheating too much, till it turns off suddently. Even if I let it in an idle state it becomes very hot, like 70 °C, and if a do anything (like play chess) it rises the temperature till 90-100 °C and turns off.
I am pretty sure that it is not a hardware problem, because I can use Windows 7 with no overheating (it becomes a little hot too, but supportable)
I Hope you can give me some help, guys. I really like Ubuntu, but i can not use it in this state. I will appreciate any reply, even if you just want to say that you have the same problem.

My laptop specifications are listed below:

Name: **Dell studio 1557**
Processor : **Intel Core i7 720-QM 1.60--2.80GHz**
Memory : **4 GB DDR3 1333 MHz**
MotherBoard Shipset : **Intel Ibex Peak-M PM55, Intel Lynnfield**
Graphics Card : **Ati Mobility Radeon HD 4570 512MB**

---

### Post by cj.surrusco on 2010-08-15
You might want to use frequency scaling. You can do that easily by adding the CPU Frequency Scaling applet to your panel. Set it to "On Demand" so that your processor will underclock itself when it has light load.

Edit: I noticed that you have a multi-core CPU, so you have to add four applets and change the settings so that each core has it's own applet.

---

### Post by wojox on 2010-08-15
Are the fan and cooling ports dusty at all? Are the fans kicking on?

---

### Post by cj.surrusco on 2010-08-15
I was looking over the specs for your CPU, and I wonder if the turbo boost has something to do with it. A i7 is going to get really hot running at 2.8ghz, especially with laptop cooling. Maybe you could try disabling the boost in the bios?

---

### Post by wojox on 2010-08-16
Maybe you should try the 32 bit version. That's what I installed on my Dell Studio, even though it's 64 bit.

---

### Post by Hemenesgard on 2010-08-16
> You might want to use frequency scaling. You can do that easily by  adding the CPU Frequency Scaling applet to your panel. Set it to "On  Demand" so that your processor will underclock itself when it has light  load.

Edit: I noticed that you have a multi-core CPU, so you have to add four  applets and change the settings so that each core has it's own applet.     I will try this.

> Are the fan and cooling ports dusty at all? Are the fans kicking on?     The fan ports are not dirty, actually they are very clean. And it is spinning normally.

> I was looking over the specs for your CPU, and I wonder if the turbo  boost has something to do with it. A i7 is going to get really hot  running at 2.8ghz, especially with laptop cooling. Maybe you could try  disabling the boost in the bios?     I wont try this because i bought a core i7 to have high performance. Doing this maybe really low the temperature, but that would be palliative, wont really solve my problem. 

> Maybe you should try the 32 bit version. That's what I installed on my Dell Studio, even though it's 64 bit.     I will try this too, but now, after having read several foruns, I really start to think that migth be a hardware problem. Its happening with lots of Windows users too. Be what appears, it is related with core i7 processors.

---

### Post by cj.surrusco on 2010-08-16
> **Hemenesgard said:**
> 

I wont try this because i bought a core i7 to have high performance. Doing this maybe really low the temperature, but that would be palliative, wont really solve my problem. 


The reason that I suggested this was to see if the problem lied within the speed boost. I though that the boost might be occurring when not needed. You should try disabling it just to see if it is, in fact, the problem.

---

### Post by Hemenesgard on 2010-09-02
Hi guys. I installed the 32-bits version, and used the CPU frequency applets but nothing helped me, still overheating till shutdown. I am pretty sure that is a hardware defect. Something is wrong with this model, Studio 1557. At least i can still use Windows 7, very very hot, but usable.

---

### Post by Cypress421 on 2010-09-02
Stick with Ubuntu 64-bit if you have 4GB or more RAM, but look in the BIOS if you can find any throttling options for turbo boost, otherwise use the frequency scaling. Your Core i7 will be used to its full potential if necessary, but otherwise underclocked. Try out the different scaling options.

---

### Post by anupcshan on 2010-09-27
I've had the same issues too. But my system runs at ~45-55°C under no load.
You could try propping up the rear of the laptop with a book or something similar to ensure better ventilation (make sure the air ducts at the back are not blocked).

---

### Post by c00lwaterz on 2010-09-28
I have same problem getting 80 deg celcius and above. even idle. I notice the fan is not running. The GPU gets hot and no fan. I tried many help and other distros but nothing works.

Toshiba m900.

---

### Post by cj.surrusco on 2010-09-28
> **c00lwaterz said:**
> I have same problem getting 80 deg celcius and above. even idle. I notice the fan is not running. The GPU gets hot and no fan. I tried many help and other distros but nothing works.

Toshiba m900.
You might want to suspend usage until you figure that problem out. It's not safe to run a CPU without a fan, and temperatures above 80C can really damage your computer.

---

### Post by Hemenesgard on 2010-10-24
Just to update things about the Dell Studio 1557.
I installed the new version, 10.10, and now its working a little better. 50- 55 °C at idel state,and 65-70°C when watching movies on youtube. But it still getting hotter when it needs more processor power, more then 90°C. So I still can't use my core i7 at maximum.

PS: What program you guys use to see the temperature? i was using the XSensors, intalled by the software center. but it gives only two temperatures. Compared to Windows programs i used, its  very poor in information.

---

### Post by kkamil on 2010-11-15
Hi, I have the same problem with overheating (Dell Studio 1557, Core i7, Radeon 4570).
I was checking the temperature using "sensors" command and currnect CPU clock by "i7z".

The main problem is ATI driver - if driver is ON than temperature can reach even the critical level (it happened to me few times). Now i'm using only default video drivers and temperature is (still height) +/- 70 °C, but at least computer is not turning off.

---

### Post by TBABill on 2010-11-15
@ OP - Are you by chance running Firefox with ubuntu-restricted-extras installed? One thing that can help with the heat as well is, if you are running Firefox to watch videos, to install Lovinglinux's addon called Flash Aid. It will look at your firefox version and flash versions, then uninstall the 32 bit and install the 64 bit if you're on a 64 bit system. It doesn't make a huge difference, but you should see some performance and temp improvement.
 
Also, do you run open java or sun java? Sun Java will help a small amount with the heat issue as well when you are using any apps or sights utilitzing java. I usually remove the iced tea plugin and install the sun java plugin instead. 
 
Sounds like you already have freq scaling working properly so there's little else that can be done, especially if you are now on Maverick with the 2.6.35 kernel which appears to be running cooler on my Dell Inspiron 1564.

---

### Post by TBABill on 2010-11-15
@OP - also, are you sure you're running the ATi driver and not the open source driver? That could make a huge difference. Sometimes people install the driver but the system is not actually using it so I'm taking a shot in the dark.

---

### Post by dellboy1557 on 2011-03-12
I realise that this is an old post, but I have only just seen it having had this problem with a Dell 1557 i7 for some time and having just found the fix for it.
It is definitely a hardware problem, due to poor heat transfer from the GPU to the heat-sink. If you install a 0.9 mm 35 mm x 14 mm copper shim between the Video Ram and cooler and a 0.7 mm x 20 mm x 20 mm ship between the GPU and cooler, bed both and the CPU cooler with good quality thermal paste and your temperatures will reduce by 20 degrees. Don't believe me, try it. I didn't believe it either, but it has worked like a charm. Quieter, no more blue screens of death, shut-downs, etc. If you have good diy skills, 22mm pipe is 0.9 mm wall thickness and 15 mm is 0.7, so what are you waiting for? Otherwise, search ebay. Trust me it works and the Dell 1557 i7 will become the mega powerful full HD video display gaming laptop you thought it was but never delivered.

---

### Post by Hemenesgard on 2011-03-12
Hi man! 20 degrees is really incredible! Can you tell us your room temperature please? ( maybe you live in one of the earth poles, hehehe.) And can post some pictures of what you did, and how you did it? 
Finally some hope!!!
Thanks you for posting. 

(My Studio 1557 has another problem now, the screen just do not give any image. And  if I keep pressing the kyes for a while it starts to beep. I need to fix this first, but i will definitely try what you said.)

---

### Post by Hemenesgard on 2011-03-23
You were rigth! I did the modifications you said and now the temperature is low. But i used 0.5mm thick copper sheets, didnt find the 0.9 and 0.7mm.
Comparison:
Before
idle state = 55-65
playing blue-ray movie = growing till 100 and shuts dow
playing ubuntu chess pc vs pc on hard = gronwing till 100 and shuts dow

After
idle state = 41-45
playing blue-ray movie = 62-67
playing ubuntu chess pc vs pc on hard = 80

thanks for the advice!

---

### Post by Yellow Pasque on 2011-03-23
I can't really tell if you folks are using open-source ATI radeon driver or proprietary (fglrx/Catalyst). If you're using open-source, make sure you turn on power management: [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

---

### Post by laith_91 on 2011-03-23
try the 32 bit version

---

### Post by Hemenesgard on 2011-03-24
I was using the Catalyst driver
And I already installed the 32 bits version. I can't tell the difference. Seams that it was a hardware problem, like dellboy1557 said.

---

### Post by Mothluin on 2011-04-29
> **Hemenesgard said:**
> You were rigth! I did the modifications you said and now the temperature is low. But i used 0.5mm thick copper sheets, didnt find the 0.9 and 0.7mm.
Hi!
I'm new to these forums; actually, I just signed up to know a bit more about this issue.
My brother has had a Dell Studio 1557 for more than a year now and the overheating problem has always been there. Recently we experienced frequent thermal shutdowns, making the notebook unreliable to use.
Since we are out of warranty (and even if we weren't, a motherboard replacement wouldn't solve the problem; hence calling Dell Support isn't worthy... or is it?) we wanted to apply this "hardware surgery" on our own.
Could anyone give us some more details on how to do it and maybe post some clarifying pictures?

Many many thanks!
Paolo

---

### Post by Hemenesgard on 2011-05-01
You will need to be courageous and disassemble all your laptop, because its not easy to reach there.
Follow the link below, and read the "Service manual" to know how to diassemble your laptop
[http://support.dell.com/support/edocs/systems/studio1557/en/index.htm](http://support.dell.com/support/edocs/systems/studio1557/en/index.htm)
Try to find the best copper shim you can. And by "best" i mean flat, and well polished. When you pass your fingers through the surface it need to be smooth like a glass surface, if its not, buy a fine sandpapers and sand it a little bit. Remember, well polished shim will means better contact to both surfaces, the chip one and the copper shim, and that will means better heat transfer.
The thickness of the shim should be 0.9mm, as was said in the thread, ( in my case, I used 0,5mm one, and I think thats why i couldnt get less 20 degrees, but definitly 0,5mm will help your overheating problems, like it did to me.)
I was a little confused when i read this solution, where to put the shims, but when you diassemble the laptop it will be self explanatory. 

[IMG]http://images.orkut.com/orkut/photos/OgAAAGg0eCJPe1DHtTXIHGR9GamOo10ld6E-r4FXMWY_JurMKllhkO_ThC5szcWOqt8IA6g2acCRiuZbXdZrYdCPzKgAm1T1UHsz63xSt_S7HDZwvjAyk9xXbC5v.jpg[/IMG]


[IMG]http://images.orkut.com/orkut/photos/OgAAAF01S8jpSv-5ZWxbIIitQ99ysMcJz2TTyWST1b92ifrzqIMPPbvbwzgQ58EjoLG51BGSJw0Egs3s5IOeTx1MV2UAm1T1UD6TnHGOE5Iv5R1G1sXQeGYkb2WB.jpg[/IMG]

Dont forget to use thermal paste in all the sufaces of the shims and chips

---

### Post by Mothluin on 2011-05-04
Wow! Thanks a lot for your help!
Just one more question before I proceed: dellboy1557 mentioned 2 different copper shims, hence I assume they shoud be placed as illustrated below (yellow rectangles).

[IMG]http://img854.imageshack.us/img854/1593/ogaaaf01s8jpsv5zwxbiiit.jpg[/IMG]

Is it right?

Thanks again.
Paolo

---

### Post by Hemenesgard on 2011-05-05
No, that's wrong, you wont put a shim at the processor, leave it alone, just put some thermal paste. The shims that dellboy1557 mentioned is for the ATI graphics card only.(that is integrated on the motherboard) One to the chip itself and the other to the memories of the chip (they are black retangular chips). I tryed to show you below, in the photo. And remove the rubber thing between the chips (they were there to help the heat transfer, but with the shims they will be useless, and if you keep them, it will be worse). I tryed to show where the shims will be in the photo below. I could diassemble my laptop again and take some pictures, step-bystep, but since i have no more thermal paste i wont do it.
[IMG]http://images.orkut.com/orkut/photos/OAAAAFhXwaLsffpKM-CcUB28xytpMHW-TXmvKCCil9AePsjug03cdnP3Rs0205Biad1jCWJrlUu0ThLQugLhihm7pGYAm1T1ULaZdxtVh7BSuZURMXboh_JQGmZS.jpg[/IMG]

---

### Post by Mothluin on 2011-05-12
Again, thank you.
Your image was pretty much self explanatory.
As soon as I have some time I'll go for it and let you know about the results! ;-)

Paolo

---

### Post by ash47 on 2011-05-18
Hi,
Is there a chance that the copper shims might slip out and short something? Do they sit tight enough?

---

### Post by Zorrothustra on 2011-05-31
I was considering getting these copper shims, but it would be difficult to get these and the thermal paste where I live.

I however started disassembling the machine following the Service Manual mentioned higher in this thread because I thought dust might be a problem. I use my laptop for about 14 months now and live in a pretty dusty environment with temperatures mostly above 30. But I never had a unsolicited shutdown until a few months ago, while I was running basically the same programs.

I disassembled the laptop and found a lot of dust inside. Besides the dust "cooked" to the fan blades and the cooling system, I took out two  "dust balls" from the iron casing the fan fits in. 

I just had a test drive. Rendering audio, batch picture tagging, multiple browers,... basically as much stuff open as I could thing of put to work. The hottest it gets now is just over 60°C ! Before cleaning it ran frequently above 80, sometimes close to a 100°C and unsolicited shutdowns.

I'll give it a go like this. If it starts heating too much again I'll reconsider getting the shims. But I'm cool enough for now...

BTW: running 64bit 11.04 Ubuntu & ATI/AMD proprietary FGLRX graphics driver on Dell Studio 1558

---

### Post by ash47 on 2011-06-01
Hi Zorrothustra,
try running a game, like Quake or Unreal tournament, just opening multiple windows is not going to stress the GPU.

---

### Post by Zorrothustra on 2011-06-08
Hi Ash47,

I don't run games like the ones you mention but I had an overheating issue anyway when I was doing multiple operations at the time. Mostly when editing audio in Ardour or tagging pictures in DigiKam, but not exclusively. Sometimes it overheated with just a number of programs opened, while they weren't actually doing any significant operation at the time.

Again, when you're there anyway to place the copper shims, consider cleaning your fan. The dust stuck on the fan blades and around the fan was impressive, not to mention the two dust balls inside the fan outlet.

---

### Post by jflinux on 2011-06-21
My xsensors say 63 with light load and 74 degrees celcius under heavy full screen video playing.   I want to clean the heatsink and fan to get rid of dust.   The one video I saw showed the guy taking the motherboard out to get to the heatsink.  Can you just take off the plastic back cover to clean the heatsink?  Seems like a lot of work to take the mobo out to clean the heatsink?

---

### Post by Zorrothustra on 2011-06-22
jflinux,

Yes it is quite some work, took me about 4 hours or more to get the job done following the Dell Service Manual: [http://support.dell.com/support/edocs/systems/studio1557/en/index.htm](http://support.dell.com/support/edocs/systems/studio1557/en/index.htm) 

Anyway it was worth it cause I'm still running quite cool.

Make sure you have an appropriate fine screwdriver and a small brush to clean of the dust. I had bought a can of compressed air as well, but the dust stuck so much to the pieces that I doubt it was worth the money. 

Have fun !

---

### Post by abhineet on 2011-06-25
Hi Hemenesgard,
 
I am facing the same problems with my Dell Studio 1557. I am out of warranty and I want to try out the solution you proposed. But I stay in a locality where the coppr shim is not readily available. What are the other options for solving this problem?
 
Thanks.
#[**22**]("http://ubuntuforums.org/showpost.php?p=10597354&postcount=22") [Hemenesgard]("http://ubuntuforums.org/member.php?u=907227")

---

### Post by ash47 on 2011-07-01
Abhineet,
When your laptop is hot and the fan is spinning, place your hand next to the heatsink (top left corner, just below the screen). Can you feel the air blowing out from the heatsink fan?
If not then you might want to consider cleaning the dust from the heatsink so that air can flow freely. This surely will make a significant difference.

As for the metal shims, you can make them yourself if you can get hold of any old copper heat sink.

---

### Post by Hemenesgard on 2011-07-01
Hi Abhineet
The most important issue on this dell studio 1557 is that there is a gap between the graphics chip and the heatsink. If you disassemble your laptop you will see that they put something there, looks like a rubber flat square, to fill the hole. But this rubber is very bad in conducting the heat out the chip, and it cracks over time, becoming useless. The copper shims are a good idea to solve the problem. It is not perfect, but helps a lot. Since you cant find the copper easily, you can put any metal you can find, because all metals conducts better then the air. so, just find something to put there and make contact between the 2 surfaces. It really dont need to be exactly the size and thickness that the guy said in the post, because you can screw the heatsink a little less, or a little more, to match the thickness of your metal, and it will be fine.

---

### Post by papaapa on 2011-07-08
Hello!

I use Dell Studio 1557 too. I have the temperature problem too. Here i explain it: [http://ubuntuforums.org/showthread.php?p=11025614#post11025614](http://ubuntuforums.org/showthread.php?p=11025614#post11025614)

I will be happy if you can help me.

Thank you!

---

### Post by abhineet on 2011-07-11
Thanks for replying guys.
 
I found the copper shims and got them shipped from UK. I just now fitted them in as told over the GPU, but sadly i don't see any difference in the temperatures. Its still heating up like crazy. I really had expectations from this. :(
 
Details:
 
I fitted two copper shims - 
1. 0.7mm 20mm x 20mm - I fitted this over the GPU.
2. 0.9mm 35mm x 14mm - Over the memory modules.
 
You were right in saying that there is some rubbery material put there, which is now relaced with the copper shims.
 
Anything I might have done wrong? What else can I try?

---

### Post by abhineet on 2011-07-11
Also, Ash47, the fan is working fine.

---

### Post by Hemenesgard on 2011-07-11
abhineet, you just placed the copper shims there, without a thermal paste?

---

### Post by abhineet on 2011-07-11
Oh no, I did exactly as told. I did use thermal paste. In fact, I even removed the old one from the Intel processor and put new paste there

---

### Post by jaxxed on 2011-08-01
This won't help the Hardware Shim solution, but I wonder if those experiencing this problem can check the following:

(these commands are all 'cat' which writes the contents of the file to screen.  You may need to use sudo if your user doesn't have read access to the files)
1) Discover what power method is being used by your radeon driver:
you:~$ cat /sys/class/drm/card0/device/power_method
profile

2) If 1) says 'profile', then what profile is being used?
jaxxed@noir:~$ cat /sys/class/drm/card0/device/power_profile
auto

3) what does you card think it's temperature is?
jaxxed@noir:~$ cat /sys/class/drm/card0/device/hwmon/hwmon0/temp1_input
68500

- Note that the card may not be card0, but rather card1, and the hwmon0 may be a different number as well.  if you need to just cd into the directorys and ls them to see what values are chosen.

Ok, so here's the deal.  there are two methods: 'dynpm' and 'profile'.  DynPM does it's own magic to make decisions about.  There are various different profiles.
All of this is listed on the [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature) link that was passed above.

This information won't fix anything, but it will let you know what the driver thinks it is doing.

If you're using KDE, then there is a nice little plasma widget that let's you control this stuff.

---

### Post by rjw989 on 2011-08-02
I had same problem, high temp and fan running all the time in Ubuntu and Kubuntu.  Windows was fine.  For me it turned out to be the ATI graphics.  I activated or installed the ATI proprietary driver instead of the open source one and it solved my problem.

---

### Post by Angelsoul on 2011-08-31
Hi all.
I tried  all yours solutions, but nothing.
The temperature of my cpu is 65°-70° in idle and over 90° in work.
Sometimes the Operative System goes in crash because reaches the critical temperature and the pc shutdown.
Another problem is that when the power is off and use only the battery, the system freeze, the sound goes into loop, and i can only restart with power button.

I contact the dell support and i hope they can resolve my problem!

With windows the temperature is high, but the carsh does not occur often, as in ubuntu.

Sorry for my English!
I hope that someone can help me!

---

