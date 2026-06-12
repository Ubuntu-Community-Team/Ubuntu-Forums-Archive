---
title: "Drobo S not recognized and best practices"
date: 2011-05-26
forum: Hardware
---

### Post by SpaceBas on 2011-05-26
Good morning folks,
I am building a new server rig and was feeling pretty good about my choices until my shiny new Drobo S arrived. Without a doubt, its a slick piece of hardware. However, the latest firmware seems to be presenting some problems with drobom in the drobo-utils package. 

My ultimate goal is to use esata for the transport. However, I first wanted to increase the LUN size to something greater than 2T. When I plug the device into my existing 11.04 server (so I can set it up and migrate my files while I await more part) it is seen as two 2tb drives. Currently I have a mix of disks in the device: 2 x 2T, 1 x 500G, 1 x 320G... so not exactly 4T in total storage. 

From here, I understand I have a few options. One is to leave the LUN size as is and use something like LVM or MHDDFS to concatenate the storage. More on that later. The other option is to increase the LUN size using the drobom commandline tool. 

According to the sourceforge page for drobo-utils, when Data Robotics updates firmware, they often change the device ID, making the scanning process challenging. That's my current issue. This Drobo S shows up as "USB 3.0   " (note the trailing spaces). I discovered that by running:

```
drobom -v 16 status
```

Again, according to the sourceforge page, I should be able to specify the device ID using the -s flag. The -s flag appears to be invalid. Any variant of the following simply returns the help text
```
drobom -s 'USB 3.0' status
``` (I've tried no quotes, double quotes, trailing spaces, etc). 

Any ideas on this first issue? Is there some kind of workaround for these new drobos and drobom with the USB 3.0 identifier? 

Now, on to best practice. Am I right to want one big LUN that I can format into ext3? Or... as some suggest... am I better off with LVM? Frankly, I don't know LVM well at all, but I've lived for 5 years with mdadm so how bad can it be :D - I played around with this method last night, I created a group out of the two volumes from the drobo and then formatted the space and have copied some files. Seems ok? 

Others suggest mhddfs... a fuse filesystem which concatenates multiple directory structures into one. 

If performance is reasonably equal then my chief concern is data protection and making sure the Drobo is working the way it is intended. That is to say, with an LVM, I'm under the impression that, in my instance, I'll allocate 4T since it appears as 2 x 2T drives which is in fact more than the total amount available for storage. So what happens if I try and *use* more than the 3.whatever T I actually have? Since it seems I may not have access to the drobom utility, am I flying blind and risking data corruption?  Conversely, if I use mhddfs how does it know which 2G "disk" to ultimately put the files on to? 

To build on that question: The drobo currently shows as /dev/sdg and /deb/sdh  ... both appear as 2T drives. However, one may be 2T but the other is only, say, 1.2T...if I format those both as ext3 and then pull them into one virtual drive via mhddfs, and copy a file into that virtual drive, how does it know which one to use first? What if it tries to put 2T onto the /dev/sdh which is actually only 1.2T.... 

Or do I totally misunderstand the Drobo concept - does the device itself manage that part of the equation? If that is the case, again, how do I keep the system which thinks there is more storage than available for writing more than is actually available? 

whew! long post - really grateful for any thoughts or suggestions this group of experts may have!

---

