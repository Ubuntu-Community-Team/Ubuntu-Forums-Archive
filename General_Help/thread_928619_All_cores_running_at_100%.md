---
title: "All cores running at 100%?"
date: 2008-09-24
forum: General Help
---

### Post by B3Nji on 2008-09-24
Hey,

When I go into system monitor, then click the resources tab it shows all of my cores running around 95-100% ! 1.36 GB of ram also being used out of 4 GB. Surly that cant be right, my system is not doing anything? All that is running is avant windows navigator and toby boy in the system tray.  

If I check the Processes tab I see that the most CPU % is being used by one process is just 3% ?

Can someone tell me whats going on? Is it some kind of bug? 

Thanks for all your help.
Ben

<To fix I used the "top" command. found out it was BIONC>

---

### Post by lovinglinux on 2008-09-24
To see the process that is overloading your system run this on a terminal:

```

top
```

Post the results.

---

### Post by anotherdisciple on 2008-09-24
Yes, run top as mentioned above...

Also, try to turn off things that you don't use. Go to (System > Preferences > Sessions) and uncheck programs that you know you aren't using (ex. evolution alarm notifier? I don't use it).

Turn off services by going to (System > Administration > Services) and turn off whatever you don't use (ex. bluetooth if your computer doesn't have the ability to use it).

Also, if you don't need indexing... turn that off... I hate it personally and it gives a lot of people issues.

---

### Post by B3Nji on 2008-09-24
> **anotherdisciple said:**
> Yes, run top as mentioned above...

Also, try to turn off things that you don't use. Go to (System > Preferences > Sessions) and uncheck programs that you know you aren't using (ex. evolution alarm notifier? I don't use it).

Turn off services by going to (System > Administration > Services) and turn off whatever you don't use (ex. bluetooth if your computer doesn't have the ability to use it).

Also, if you don't need indexing... turn that off... I hate it personally and it gives a lot of people issues.

Thank you both for your input. 

Dont I feel stupid. I installed Bionc (that computer network application for SETI etc) a few weeks back. I completely forgot about it, seeing as I thought I closed it down, and I didn't realize it ran on its own on reboot. The process does not show up in resources.
But that "top" command worked a treat. 

Anyway, its that. Stupid  thing has been running on its own taking up all my recourses! lol. 

Thanks again for your help :)

---

### Post by anotherdisciple on 2008-09-24
Cool... can you mark this thread as solved please? Instructions are in my signature.

---

### Post by lovinglinux on 2008-09-24
> **B3Nji said:**
> Anyway, its that. Stupid  thing has been running on its own taking up all my recourses! lol. 

That is the objective of that application, using your computer resources to download and process their data. It should have at least a way of configuring when and how much CPU power it would eat form your machine.

Nice that you figured it out.

---

