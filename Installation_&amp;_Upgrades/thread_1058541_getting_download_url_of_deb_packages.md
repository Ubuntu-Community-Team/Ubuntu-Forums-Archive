---
title: "getting download url of deb packages"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by brijith on 2009-02-02
Hai All,

I would Like to know how to get the url of the deb package. What I have with me is a list of package names. ( like  **python-serial_2.2-4_all.deb**) I would like to get the url corresponding to the package name so that I can download then using **wget**...

Please Help Me !!


[COLOR="DarkOrange"]**Thanks**[/COLOR]

---

### Post by tommcd on 2009-02-03
If you are looking for the url for Ubuntu .deb packages it is here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Just pick your version of Ubuntu from the list and you can browse the different categories. Or use the search function to find your packages.

Your /etc/apt/sources.list has the urls of the Ubuntu mirrors you are using to install packages via synaptic or apt-get.

---

### Post by brijith on 2009-02-03
> **tommcd said:**
> If you are looking for the url for Ubuntu .deb packages it is here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Just pick your version of Ubuntu from the list and you can browse the different categories. Or use the search function to find your packages.

Your /etc/apt/sources.list has the urls of the Ubuntu mirrors you are using to install packages via synaptic or apt-get.

[COLOR="DarkOrange"]**Thanks for Your Response**[/COLOR]


But the thing is I have so many number of filename with me, about 700, So would like to write a script...

And I can't relay upon synaptic since I have to install the packages in a system which has no internet connection....

---

### Post by tommcd on 2009-02-03
> **brijith said:**
> [COLOR="DarkOrange"][
But the thing is I have so many number of filename with me, about 700, So would like to write a script...
And I can't relay upon synaptic since I have to install the packages in a system which has no internet connection....

Sorry, but I can't help you with writing a script.
You can download the packages you need at [http://packages.ubuntu.com](http://packages.ubuntu.com). You can then transfer them to the computer via a flash drive or CD-R or whatever. You will have to manually account for all dependencies. For example, the page for  python-serial lists python and python-central as dependencies:
[http://packages.ubuntu.com/intrepid/python-serial](http://packages.ubuntu.com/intrepid/python-serial)

---

### Post by Partyboi2 on 2009-02-03
> **brijith said:**
> [COLOR=DarkOrange]**Thanks for Your Response**[/COLOR]


But the thing is I have so many number of filename with me, about 700, So would like to write a script...

And I can't relay upon synaptic since I have to install the packages in a system which has no internet connection....
If you are trying to install or upgrade packages without a internet connection you can use "generate package download script" that  will create a script that uses wget.

[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

### Post by brijith on 2009-02-03
> **Partyboi2 said:**
> If you are trying to install or upgrade packages without a internet connection you can use "generate package download script" that  will create a script that uses wget.

[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)


But when a fresh ubuntu system is installed there won't be all packages listed in the synaptic. I think we can only make download scripts for packages listed in the synaptic. Is there any method to get all packages listed in synaptic ......


[COLOR="DarkOrange"]**Thanks**[/COLOR]

---

### Post by Partyboi2 on 2009-02-03
> **brijith said:**
> But when a fresh ubuntu system is installed there won't be all packages listed in the synaptic. I think we can only make download scripts for packages listed in the synaptic. Is there any method to get all packages listed in synaptic ......


[COLOR=DarkOrange]**Thanks**[/COLOR]
You are correct, I forgot about that. Another option is to use [keryx.]("http://keryx.betaserver.org/") A howto is [[COLOR=Blue]here[/COLOR]]("http://crashsystems.net/2009/01/keryx-tutorial/")
The only thing you would need to do before using that howto is to Open Software Sources and enable all the repos you want,  it will error out when you close Software Sources as it tries to update, but that is ok because keryx only needs the repos enabled to work.

---

### Post by hammer v2 on 2009-02-04
also check out superdeb
[http://code.google.com/p/superdeb/](http://code.google.com/p/superdeb/)

It goes officially "Live" this weekend. :)

---

