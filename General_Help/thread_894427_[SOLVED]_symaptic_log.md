---
title: "[SOLVED] symaptic log"
date: 2008-08-19
forum: General Help
---

### Post by jesse c on 2008-08-19
after many,many hours of my and forum community time i have now repaired my system after i exprimented with different settings in synaptic and deleted something that crashed my system.Now i want to know is there some command line that will bring up all the applied settings in synaptic so i can print out and compare settings the next time i do this,'cause i know i will,im the type that doesnt leave well enough alone JESSE C

---

### Post by sandy123 on 2008-08-19
Hi,
This is sandy,ok nevermind i have ubuntu running but heres another problem.....sites like youtube,runescape,etc. wont work without plug-ins. when i try to go there it tells me to click here to install these plug-ins but when i do it says "cannot find (name of thing i selected)"
========================================================
sandy
[Maryland Drug Treatment ]("http://www.drugtreatments.com/maryland")

---

### Post by drs305 on 2008-08-19
> **jesse c said:**
> after many,many hours of my and forum community time i have now repaired my system after i exprimented with different settings in synaptic and deleted something that crashed my system.Now i want to know is there some command line that will bring up all the applied settings in synaptic so i can print out and compare settings the next time i do this,'cause i know i will,im the type that doesnt leave well enough alone JESSE C

I am not completely sure what I post is what you actually want. You mention synaptic and settings several times. Synaptic doesn't control app settings per se, just the packages that are installed on your machine. If you are looking for something that will preserve all your configurations, this won't apply. 

If you want a list of all the packages synaptic/dpkg has installed on your system, you can run the following command to get a list. This will create a simple text file, "package-list", on your desktop.
```

sudo dpkg --get-selections >~/Desktop/package-list

```

If you should wish to reinstall all these apps at a later date, you can import the list back into dpkg to reinstall the packages:
```

sudo apt-get update
sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/package-list	
sudo apt-get dselect-upgrade

```

---

### Post by sofasurfer on 2008-08-22
I have a working system. I did a "sudo dpkg --get-selections > media/disk/package-list".

I then created a testing installation on a differant drive. I intend to recreate my working system on the testing system. 

I did not update anything or edit my sources list to be like the one on my working system. Do I need to edit my sources list before proceeding?

After trying instructions to install the software from my package list from many threads I tried your thread and started to see progress.

I followed these steps...

sudo apt-get update
sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/package-list	
sudo apt-get dselect-upgrade

When I got to the dselect step things proceeded untill it got to google earth. Then the licensing agreement came up and that is where I got stuck. I could not get past it. There is an "ok" prompt at the bottom of the agreement but it does not do anything. 

Any idea how I can get past that so I can see further progress?

---

### Post by drs305 on 2008-08-22
> **sofasurfer said:**
> When I got to the dselect step things proceeded untill it got to google earth. Then the licensing agreement came up and that is where I got stuck. I could not get past it. There is an "ok" prompt at the bottom of the agreement but it does not do anything. 

Any idea how I can get past that so I can see further progress?

It's been a while since I installed GoogleEarth but I believe that once you see the "OK" you have to tab to it and then hit ENTER. That is often the way apps that require an agreement of some sort work in linux.

---

### Post by sofasurfer on 2008-08-22
O dang!! I bet thats the only key I did not try. I'll check it out after work. Thanks for the reply.

---

