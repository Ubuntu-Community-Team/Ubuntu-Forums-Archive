---
title: "Vgaswitcheroo"
date: 2011-09-24
forum: Hardware
---

### Post by cosmicgr on 2011-09-24
Hi all
I have a HP dv7 latptop with dual graphics - Intel HD and ATI Radeon 6770m.
I do not need the ATI card in ubuntu, and want to disable it completely, as right now it is just eating power and doing nothing. I have not installed any driver from ATI.
I had followed some threads which show how to do this by changing some settings in VGASWITCHEROO file. However I do not have such a file in my system!

I have also booted with radeon.modeset=1, yet no such file
Also with modeset=1, no file.

Can anybody help me to power off radeon chip completely?

---

### Post by ..sam.. on 2011-09-24
Have you had a look at these instructions;
[http://asusm51ta-with-linux.blogspot.com]("http://asusm51ta-with-linux.blogspot.com/")
May may be useful.

---

### Post by .... on 2011-09-25
I think what you want is not vgaswitcheroo, but acpi_call: [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by Clicksights on 2011-09-27
Meet the transformers ;)


I have also an Optimus set-up on my MSI X460DX
I took me a bit but i now am from 60Fps up to 600Fps if i use bumblebee. :p
Bumblebee works great if you want to use the power of your extra graphics card.

You can switch your extra card off with the help of ironhide.
That will increase the battery bij a few hours! :p
I didn't try Ironhide yet.

the inventor:
[http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/)
ironhide
[https://launchpad.net/~mj-casalogic/+archive/ironhide/]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/")
bumblebee:
[https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)

Some laptops have a bios option to switch the extra card off.
Hope this helps.

(You need both drivers installed, for both the onboard card and the extra card!)

my 2 beans...

---

### Post by cosmicgr on 2011-09-27
Thanks guys, actually my BIOS does not have the option for a "fixed mode". So I want to know can VGASWITCHEROO, ACPI CALL, IRONHIDE etc work if there is no option for switchable cards in the BIOS? I do not want to update my BIOS. :(

---

### Post by .... on 2011-09-27
> **cosmicgr said:**
> I do not want to update my BIOS. :(
Then I guess you really don't want to fix the issue....

---

### Post by realzippy on 2011-09-27
> **cosmicgr said:**
> So I want to know can  ACPI CALL work if there is no option for switchable cards in the BIOS? I do not want to update my BIOS. :(

Yes, *if* it works, it is not related to your BIOS version.

---

### Post by Clicksights on 2011-09-27
If a bios update is 100% adding a possibillity to switch the extra card off, i would do a bios upgrade.
:p
The bios does not need to support it to make bumblebee or ironhide work.
Do keep in mind that it is not possible to let ironhide and bumblebee work together.
I made the choice for performance, thus bumblebee.
(i like to game every now and than... ;)  )

I do want to try ironhide, sadly it is not so well documented as bumblebee.
But if i read it ok, ironhide will switch the extra card off, and still has an optirun function
for using the extra graphics card.

I will try to make ironhide work this week and post the results.

---

### Post by realzippy on 2011-09-28
Bumblebee stable meanwhile also contains the framework for switching off the
nvidia-card,means,the ACPI-call stuff.
To test if it works for your machine,you not need to install BB or IronH,
just run the test.sh script after inserting the module.

Anyway,if you need help with this,send me a pm.
Have fun..

---

### Post by Clicksights on 2011-10-25
> **realzippy said:**
> Bumblebee stable meanwhile also contains the framework for switching off the
nvidia-card,means,the ACPI-call stuff.
To test if it works for your machine,you not need to install BB or IronH,
just run the test.sh script after inserting the module.

Anyway,if you need help with this,send me a pm.
Have fun..

I just installed ubuntu 11.10 and got bumblebee working again, :D
I want to try the APCI on/off stuff, but i am a bit lost...
My laptop is listed (MSI X460DX) so it should work.
(it did work with ironhide before in 11.04)
But how can i test it?
I can't find anything on the test script? 
A bit of help is appreciated!

I did send a pm, hopefully you will react soon, maybe here too because hopefully more people can learn from a post here. ;)

I installed the apci-call-tools, but have no idea where i should 'cd' to execute the test script...
Lol could be its just too late, ehh early! i'll check in here tomorrow after a few hours of sleep!
Before i do something stupid  :wink:

---

