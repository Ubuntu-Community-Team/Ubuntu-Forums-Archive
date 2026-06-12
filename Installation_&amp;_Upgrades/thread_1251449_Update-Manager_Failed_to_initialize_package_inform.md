---
title: "Update-Manager: Failed to initialize package information"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by Tyson D on 2009-08-27
i just realised i havent been bothered by my update manager on a daily basis like i usally do so i opened it and this is what it says:

"""An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 6 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.' """

ive began my search through the forums and bug reports but have yet to find anything. a little help or redirection would go a long way.

---

### Post by drs305 on 2009-08-27
You have an error on line 6 of /etc/apt/sources.list which prevents accessing the repositories.

Open it with the following. If you don't recognize the error, post the results:
```
gksudo gedit /etc/apt/sources.list
```
All lines in sources.list should start with either "deb" or a comment symbol (#).

---

### Post by Tyson D on 2009-08-27
i have opened said file and have not noticed anything out of the ordinary this is what it looks like:

deb Germany jaunty main restricted multiverse universe
deb-src Germany jaunty main restricted


those are lines 6 and 7 of /etc/apt/source.list

---

### Post by drs305 on 2009-08-27
Those aren't valid lines. In place of Germany there should be an http or ftp address like you probably have in your other lines. Comment them out or delete them, as they are not doing any good and are causing the errors.

You can go into Synaptic to make sure you have the proper repositories enabled, then, in the Ubuntu Software tab, go to Download From and select the desired repositories, then hit Reload. 

Here is the Ubuntu Wiki on Repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

The lines should probably look something like the following unless you have other lines for the main repositories:
> 
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) jaunty main restricted multiverse universe
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) jaunty main restricted multiverse universe



---

### Post by Tyson D on 2009-08-27
ok so synaptic didnt work because of the same problem as update-manager so after reading the repositories page i found all the 'Germany' and replaced them with the website that you gave me, everything works again!!!!!!


thanks a lot

---

### Post by drs305 on 2009-08-27
> **Tyson D said:**
> ok so synaptic didnt work because of the same problem as update-manager so after reading the repositories page i found all the 'Germany' and replaced them with the website that you gave me, everything works again!!!!!!


thanks a lot

You're welcome, and welcome to the Ubuntu forums, by the way. 

The server example I gave was just the result of selecting the "Best Server" at the moment - and of course that was from where I am located. You should probably go into Synaptic, Settings, Repositories: Ubuntu Software tab. Click on the "Download from:" box, select Other, then either choose a location near you or run the "Select Best Server" option. It will take a minute or two to run, and then offer the best real-time connection. When you hit "Close" or "OK" it will replace all the addresses in your sources.list with the new mirror site.

---

