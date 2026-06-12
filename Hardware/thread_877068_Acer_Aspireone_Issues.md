---
title: "Acer Aspireone Issues"
date: 2008-08-01
forum: Hardware
---

### Post by starkes on 2008-08-01
Hey there,

I got myself an aspireone and put ubuntu on it.


Seems like it's more than powerful enough to get the job done, i went through the info at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and got the wireless working and a few other tweaks.

however... I've been seeing major slowdowns on this thing. Opening a video, firefox window, almost anything can make the system hang for a bit. and it's a bad hang, i was copying files to it over the network and it dropped the connection when i opened firefox. it's like a total pause every time or something.

from the system monitor i dont see any serious bottlenecks, it seems like the atom blasts through things when it works, just it hangs enough that its not fun to use as a music player or for any real work.

has anyone else had such problems? any advice?

also, if the atom is single-core, why do i see two cores in the system monitor? is this some sort of "hyperthreading" going on?

thanks.

---

### Post by phidia on 2008-08-01
I have been reading about that cpu from [this page]("http://www.intel.com/technology/atom/index.htm") they do say > Intel® Atom&#8482; processors also feature multiple threads for better performance and increased system responsiveness.
It is a low power cpu but can you have low power consumption and good prerformance?
I mean outside of the advertising PR world?

But as to the hangs or freeze-ups you're seeing does anything stand out in /var/log/messages? You might need to use a special kernel with that processor. 
Unless that sounds too crazy-you can check kernel building and selecting out [here]("https://help.ubuntu.com/community/Kernel?action=show&redirect=KernelHowto").

---

### Post by hotweiss on 2008-08-01
How did it work with the preinstalled Linux? I was thinking of getting it...

---

### Post by starkes on 2008-08-05
the preinstalled linux is absolute garbage. i didnt really give it a shot but you'd see why when you get it. im sure its functional but its not layed out like a generic linux desktop, its more like a device or something... like a phone.

that said i didnt find it too too hard to get ubuntu on it, though its not without its issues.

also, has anyone had problems with the mouse? im starting to wonder if theres something just wrong with this particular machine. my left mouse button  doesnt work sometimes now and im still having issues with the pausing. i will look into this new kernel though

---

### Post by starkes on 2008-08-05
does anyone else seriously not notice any slowdown issues?

its not always epic, but it seems like a system with a 1.6ghz atom and 512mb of ram should be pretty smooth when its opening programs. my old dell 550mhz machine wouldnt crap out a network tranfer if i opened firefox

im wondering if since 8.04 doesnt even work at all with the atom, 8.04.1 isnt perfect yet or something.

anyone with anything to add please do, im not sure if my machine is defective, if its something i need to tweak out, or if ubuntu just doesnt run perfectly on it yet. and i have two days left to exchange it. (they want linpus on it when i bring it, dont make me go back!)

---

### Post by hotweiss on 2008-08-06
You can try this thread:

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=164](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=164)

I think they've gotten everything working now.

---

### Post by starkes on 2008-08-06
yeah. ive gone through all that stuff and got everything they talk about working the way they say, but my problems are elsewhere. i'm even on wifi right now and its working, but the overall experience has a lot of glitches still.

im going to put linpus back on here and exchange it and start over i guess, and then i'll know if its a defective machine or its just a problem with software or something

---

### Post by Tycox on 2008-08-06
I don't think it's related to hardware. I'm having the same issue here. I believe it's related to the kernel. The current Kernel is 2.24 if I'm not mistaken, the card reader is certainly supported staring with kernel 2.25.

---

### Post by hotweiss on 2008-08-07
> **starkes said:**
> yeah. ive gone through all that stuff and got everything they talk about working the way they say, but my problems are elsewhere. i'm even on wifi right now and its working, but the overall experience has a lot of glitches still.

im going to put linpus back on here and exchange it and start over i guess, and then i'll know if its a defective machine or its just a problem with software or something

So tempted now, NCIX has it on now for $345 with a free a 4 GB SD card. I'm just waiting for the HD version...

---

### Post by starkes on 2008-08-07
another kernel eh....it could be a software issue, but its not responsive to anything i do, though something at the kernel level could do that.

im having problems where the touchpad in general is not working right at all.

sometimes i come back to it after it's been sitting around for a while, and i touch the pad and the mouse goes crazy, it just flutters around the screen like its on crack. and then i plug in a usb mouse and have no problem with it at all.

and the touchpad doesnt go back to normal after plugging in a mouse, theres nothing you can do to trigger it to go back to normal, as far as i can tell. its just random.

---

### Post by danthegoodman on 2008-08-07
"How did it work with the preinstalled Linux? I was thinking of getting it..."

I haven't really messed around with Ubuntu on my AAone, but I have noticed some limitations with the Linux they have on it, mainly in the configuration abilities (Panels, shortcut keys, etc).

Most of those limitations have work-arounds, but do require technical know how. It's almost like this version was made for people with no computer knowledge or for those with extensive knowledge. 

If you're thinking of getting an AAone, make sure you have Linux knowledge or be prepared for a quick and dirty crash course on Linux.

As for how it works, I like it. I like the phone-like interface (which is easily customizable) and since it's based off of fc8, there are plenty of packages available for it.

---

### Post by starkes on 2008-08-07
what i noticed is this:

linpus linux is not a general OS. not enough anyways, even if it is based off one. its like using an iphone to do business work. ya just dont.

---

### Post by starkes on 2008-08-09
has anyone tried a different kernel? maybe a non-smp kernel since the atom really only has one core?

---

### Post by Kjeks on 2008-08-13
Hi!
I seem to have the same problems as you, starkes.
I got my Acer One a couple of days ago, and installed Ubuntu 8.04.1 on it after breaking the pre-installed one :)

Ubuntu seems to work pretty well on this machine, BUT I do experience the same freeze problems as starkes.
When using Firefox, the machine often hangs for several seconds. Just clicking the login form field on this page was enough to hang the machine for about 6-7 seconds.
It happens so often that it's a problem.

System monitor says I'm using 300 MB of 492 MB RAM, so that shouldn't be the problem here.

Has anyone found a solution?

---

### Post by Kjeks on 2008-08-13
After a bit of digging around, I think I found a solution.
In Firefox: enter "about:config" in the address bar.
In "filter", type "cache".
Double click "browser.cache.disk.enable"

At least that worked for me. My FF is now much faster! I think the SSD-disk may be the bottleneck.

---

### Post by starkes on 2008-08-14
nice, i'll try that out, firefox is most of the problem...

it goes well beyond firefox too though, for me. could the ssd really be THAT slow? it seems less slow and more like pausing.

does the SSD have a really long seek time or something? would it be faster to just boot from a usb key?

i'm still hoping a new kernel will iron things out a bit. I've been running folding@home on it, and it seems like it gets about 30 PPD whereas my cheap dell vostro laptop with a centrino gets 70. It only uses one core on either, so the atom is something like 1/4th the speed, which is pretty slow.

I thought it was faster than that?

---

### Post by oswaldkelso on 2008-08-26
> **starkes said:**
> the preinstalled linux is absolute garbage. i didnt really give it a shot but you'd see why when you get it. im sure its functional but its not layed out like a generic linux desktop, its more like a device or something... like a phone.

that said i didnt find it too too hard to get ubuntu on it, though its not without its issues.

also, has anyone had problems with the mouse? im starting to wonder if theres something just wrong with this particular machine. my left mouse button  doesnt work sometimes now and im still having issues with the pausing. i will look into this new kernel though

I have an acer one A150L 120GB 1GB RAM.

I really don't see how you can say the default install is "absolute garbage" when you "didnt really give it a shot" It is not the distro I would be running on it by choice, but my friend who is not a linux user found it intuitive and easy. She was even considering buying one because of this.

I will say every thing pretty much works out of the box and you can if you wish add more apps and repos ( fedora 8 ) if you want. The default install is fast and small. Just a skin for xfce really but its easy enough to  get under it. Its been very stable and I've been quit impressed by the quality feel. Left click right click and scroll wheel work, dual monitors, webcam, wifi compiz,  etc....   

Just because you want to run Ubuntu does not mean you should slag off the default install, which is clearly designed to do some thing you don't require. i.e. be easy and work for total Linux noobs. 

That said I will be replacing the default install because I normally use Debian and am used to it. I also I want as few none free applications as I can get away with. But not because its "absolute garbage"

---

