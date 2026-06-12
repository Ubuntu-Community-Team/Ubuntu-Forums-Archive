---
title: "GTX 660M nvidia Driver"
date: 2012-11-15
forum: Hardware
---

### Post by technofreak08 on 2012-11-15
Hello guys.

Hopefully someone knows a bit about the nvidia drivers. I am trying to install the drivers on a Lenovo Y580 that has a GTX 660M, running 12.04 64 bit. Everything I have tried results in the nvidia settings saying that "you do not appear to be using the nvidia x driver." I have downloaded the driver directly from nvidia and installed it, and I have done the following also.

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

I have ran the ```
nvidia-xconfig
``` but that does absolutely nothing, still results in the settings saying that I am not using the nvidia x driver. Also my resolution is stuck on 640x480 with the drivers installed. It goes back to the native 1920x1080 after I uninstall them.

I have also tried out the bumblebee drivers... and they didn't work. Though that was something else entirely. I know there are a lot of threads out there with this kind of problem, but I just have not been able to come across anything that helps.
Any suggestions or help any has to offer I greatly appreciate.

The driver that I have tried using is the 304.64 driver. The latest stable one.

Thanks

---

### Post by ubuntoobu on 2012-11-29
Not that it helps but I also have a y580 laptop with the same nVidia card and I've also done the exact same things you've mentioned without any luck.

I'm fresh out of options but if I ever do figure this out I'll post back and let you know.

Good luck.

---

### Post by gnusci on 2012-11-29
What about the NVidia drivers?

[http://www.nvidia.com/object/linux-display-amd64-295.59-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.59-driver.html)

---

### Post by Yellow Pasque on 2012-11-30
It looks like Lenovo Y580 is an Optimus/hybrid system, so you'll need to install the nvidia drivers through bumblebee (installing them directly won't work). What happened when you tried to use bumblebee?

---

### Post by ubuntoobu on 2012-12-01
Re: Bumblebee ...

Followed the instructions in this thread...

[http://askubuntu.com/questions/180104/accelerated-graphics-with-an-nvidia-card](http://askubuntu.com/questions/180104/accelerated-graphics-with-an-nvidia-card)

...and the following happened...

```
chris@y580:~$ sudo bumblebeed restart
FATAL: Error inserting bbswitch (/lib/modules/3.2.0-33-generic/updates/dkms/bbswitch.ko): No such device
[  391.369245] [ERROR]Module bbswitch could not be loaded (timeout?)
[  391.369339] [WARN]No switching method available. The dedicated card will always be on.
[  391.371361] [ERROR]Daemon already running, pid 8477
```

...then...

```
chris@y580:~$ optirun glxgears
[  402.325875] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the

[  402.325948] [ERROR]Aborting because fallback start is disabled.
```

---

### Post by Yellow Pasque on 2012-12-01
Perhaps you need to enable switchable graphics in the BIOS/EFI?..

---

### Post by carnivroar on 2012-12-01
Do a fresh reinstall of the OS then try this

[http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/)

plus my comment on the bottom (the one posted at 2012-12-01 20:57:27 EST)

No garantees but it worked on my ASUS N56VZ on Ubuntu 12.04. I have my intel GPU working and my NVIDIA 650m working with optirun command.

Good luck.

---

### Post by technofreak08 on 2012-12-02
@carnivroar I actually came across that same tutorial a couple days ago. That is the farthest I have been able to get with bumblebee. It still doesn't run right though. When running ```
optirun glxspheres
``` I get this: ```
[  113.389366] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA: Use the -ignoreABI option to override this check.

[  113.389431] [ERROR]Aborting because fallback start is disabled.

```
I have not seen this particular error before. I sent off a bug report to the bumblebee devs, hopefully they get back with me soon.
I am beginning to hate optimus machines...
@Temüjin, I don't think there is a way to disable and enable the graphics in bios.

P.S. I have also done the "lenovo hack" from here --> [https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo](https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo)

---

### Post by carnivroar on 2012-12-02
> **technofreak08 said:**
> @carnivroar I actually came across that same tutorial a couple days ago. That is the farthest I have been able to get with bumblebee. It still doesn't run right though. When running ```
optirun glxspheres
``` I get this: ```
[  113.389366] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA: Use the -ignoreABI option to override this check.

[  113.389431] [ERROR]Aborting because fallback start is disabled.

```
I have not seen this particular error before. I sent off a bug report to the bumblebee devs, hopefully they get back with me soon.
I am beginning to hate optimus machines...
@Temüjin, I don't think there is a way to disable and enable the graphics in bios.

I have seen that error before, usually when I mess around with the drivers and end up screwing everything up. 

If you start from a clean install, do exactly what the tutorial tells you, it should work. I have done it a couple of times.

It was really getting the CUDA SDK that was giving me problems.

---

### Post by technofreak08 on 2012-12-02
> **carnivroar said:**
> I have seen that error before, usually when I mess around with the drivers and end up screwing everything up. 

If you start from a clean install, do exactly what the tutorial tells you, it should work. I have done it a couple of times.

It was really getting the CUDA SDK that was giving me problems.

I will give that a shot, thanks.
I was using 12.10, you think I should just use 12.04? 12.10 seemed to work better with my system but the drives may work better with 12.04.
Probably will be a couple weeks before I can try it out since I am in the middle of finals at the moment. I will report back when I get it done.

---

### Post by carnivroar on 2012-12-02
> **technofreak08 said:**
> I will give that a shot, thanks.
I was using 12.10, you think I should just use 12.04? 12.10 seemed to work better with my system but the drives may work better with 12.04.
Probably will be a couple weeks before I can try it out since I am in the middle of finals at the moment. I will report back when I get it done.

I'm not sure. I guess it would work on 12.10 just as well. I have never used it, who knows, it's probably better. The only reason I am using 12.04 is because that's what I have on a USB that I use to install the OS.

---

### Post by Yellow Pasque on 2012-12-02
Bumblebee users were reporting issues with 6x0M nvidia chips. If you're using the latest nvidia driver, and still getting "cannot access secondary GPU", then nvidia hasn't fixed it yet.. ](*,)

---

### Post by ndstate on 2012-12-03
I ordered the Y580, so I may be able to help when it arrives.

Check out the following video, he seems to have the 660m running well: [http://www.youtube.com/watch?v=bQ3dskLgxsM](http://www.youtube.com/watch?v=bQ3dskLgxsM)

Perhaps you could reach out to him?

His contact info is listed on his Youtube page.

---

### Post by ndstate on 2012-12-15
I followed the directions [here]("http://translate.google.com/translate?hl=en&sl=sr&u=http://blog.urosevic.net/2012/10/13/2567/lenovo-ideapad-y580-nvidia-gtx-660m-ubuntu-12-04/&prev=/search%3Fq%3D660m%2Bubuntu%26hl%3Den%26client%3Dbrowser-ubuntu%26hs%3Dlp6%26tbo%3Dd%26channel%3Dfe%26biw%3D1855%26bih%3D990&sa=X&ei=iBLMUNrqAuT8yAGciYCwAw&ved=0CFoQ7gEwBA") and everything worked well on the y580.

Note that Google translate messed up some of the spacing so I had to fix that manually.  Also, be sure when you get to the git section to just use the steps at [https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo](https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo)

Let me know how it works for you all.

---

### Post by ndstate on 2012-12-19
As an update I have gotten this to work in both 12.04 and 12.10.

In 12.10 optirun glxgears returns 1500-1700 FPS.  Anyone else want to share what they have gotten for comparison?

---

### Post by ubuntoobu on 2012-12-21
> **pmp6nl said:**
> As an update I have gotten this to work in both 12.04 and 12.10.

In 12.10 optirun glxgears returns 1500-1700 FPS.  Anyone else want to share what they have gotten for comparison?

Thanks for the help, I have it working following your instructions.  My FPS is about 1070 on 12.04 LTS Ubuntu.

---

### Post by technofreak08 on 2013-01-07
Sorry it has taken me so long to reply to this thread. I did finally get Bumblebee to work properly. I followed [these instructions]("http://eternalvoid.net/tutorials/linux-optimus-gt650m/") and got it working. I used the latest nvidia drivers. Though I am really regretting getting a laptop with optimus right about now... I love my Lenovo y580 but it is such a pain. I couldn't get Quak4 to run with "optirun" which was super disappointing. One thing I was thinking of was trying just nvidia drivers by themselves to see if I could skip over the intel chip completely. Not sure if that would work though. If anybody knows anything on that let me know.

...Though I have tried installing the nvidia driver... and it didn't work out so well...

---

### Post by hadrons123 on 2013-01-18
I get 1200 FPS in (optirun glxgears -info) in Debian sid with nvidia 304 drivers with suwako bumblebee.

When I use Arch linux with nvidia-bumblebee 310 and 313.x drivers I get only 600 FPS.

fedora 18 has similar values as Arch linux.

I know optirun is not a benchmarking app, but I simply dont understand the variation in the newer drivers.

---

