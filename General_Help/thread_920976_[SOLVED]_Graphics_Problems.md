---
title: "[SOLVED] Graphics Problems?"
date: 2008-09-15
forum: General Help
---

### Post by Sabreful on 2008-09-15
Hello to all who read this;
First off it should be known that I am new to Ubuntu, (took me long enough) so I know very little, but I've read up on forums and how-to threads and what-not, so I do know *some* basics.
     Currently I am using 8.04 Ubuntu Hardy Heron.
     I have a gateway 450sx4 notebook
     My graphics card is an ATI-M6P which if I'm not mistaken is classified as an AllInWonder Radeon 7500 Series. 

The problem I seem to be running into is that I can't seem to get my visual effects out of the "None" setting. Every time I go to select "normal' or 'extra' I get an error after my screen flashes a few times saying "Could not enable effects". Without that I don't believe I will be able to run anything other than the basics.

I have compiz installed under my system>preferences>advanced desktop configuration settings. and I have also tried to use Envy to get the correct drivers. 
When I run the command compiz through my terminal to see what's going on the following comes up:
     Checking for Xgl: not present. 
     Found laptop using ati driver. 
     aborting and using fallback: /usr/bin/metacity

I think that the ati driver that's present is the OpenGL driver that comes with Ubuntu because I haven't installed any type of drivers whatsoever. It just worked.

Reading up on other things people have tried, I downloaded Envy in hopes that it would work as well. Selected to 'Install the ATI drivers' through automatic hardware detection and the following error came up:

python pulse.py ati 
root@450sx4:/usr/share/envy# python pulse.py ati 
EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Traceback (most recent call last):
  File "pulse.py", line 79, in <module>
    autoChoice(sys.argv[1])
  File "pulse.py", line 18, in autoChoice
    objects.atiinstallg(data1)
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 208, in atiinstallg
    task.drivertype()#latest, middle, oldest driver
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 863, in drivertype
    raise Exception(error)
Exception: EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.


Am I doing something wrong? Or is it my hardware? Is there somewhere I need to go or something I need to download? 
Thanks in advance

---

### Post by overdrank on 2008-09-15
Hi and welcome, you may look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
Also you may look at how memory is shared with the ATI graphics in the bios.

---

### Post by Sabreful on 2008-09-16
You rock. Any chance of explaining what 'compiz --replace &' command actually did?

---

### Post by el-mar01 on 2008-09-16
> **Sabreful said:**
> Any chance of explaining what 'compiz --replace &' command actually did?

It replaced Metacity as your window manager. Thats why the metacity --replace command replaces Compiz as your window manger.

---

### Post by Sabreful on 2008-09-16
I don't have metacity installed though, somehow it fixed it to where i can switch it to 'normal' through system>preferences>appearance and then i can use compiz... or is metacity & compiz the same? if not which one is technically better?

---

### Post by larryfroot on 2008-09-23
They both get the job done...but metacity has no fancy effects (although you can still use multiple desktops and switch between them). Compiz has the wobbly windows, spinning cube and all of that. As far as I can tell though, metacity just works straight out of the box, whilst compiz often needs tweaking - as you have found yourself doing.

---

