---
title: "Interesting apt-cache dpkg problem"
date: 2008-08-21
forum: General Help
---

### Post by kotfic on 2008-08-21
Hi everybody!

So I have a bit of a problem and was wondering if maybe someone had some ideas. First a little background:

 I am currently administering a machine in a remote part of West Africa. Ubuntu has solved a lot of server related problems for a local farmer savings and loans office. Its a bureau of about 10 computers on a LAN with a central Ubuntu samba/LAMP server. There is no internet connection in the bureau the closest connection is a 45 minute motorcycle ride away. 

The problem arises when I need to install new software (in the immediate case  tshark so I can watch network traffic on the GUI-less server). Usually I run something like 'apt-get --print-uris etc' to get the URL's of the missing packages and take the moto-taxi to the cyber and download the packages I need, bring them back and install them. I live in the town with the cyber and this means trucking out to the server, finding the uri's, riding all the way back to the cyber, downloading them, and then going back to install them. Hardly an optimal solution!

I know I can get a full list of packages dependencies and download them all,  but for any arbitrary package the list is huge (and usually mostly met by the default server installation). 

1. Is there any way to cull that list so I only have to download the ones that are not in the basic server installation? 

2. Or better is there a way to keep the server's list of installed packages on my laptop and download the required packages based on this list instead of my laptop's list? 

3. Should I just keep a repository of packages on my laptop and augment that repository whenever i want to install new software on the server and trying to keep the two in sync?  

The second solutions seems like the best but its not clear to me how one would go about doing something like. If anyone could shed some light on this it would save me a ton of money in taxi fares and an awfully sore derrier =P

Thanks so much!

---

### Post by Vivaldi Gloria on 2008-08-21
I don't know much about your problem but let me mention a few things.

1) There is a tool called apt-mirror to create a local repo:

[http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)
[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)
[http://odzangba.wordpress.com/2007/12/24/use-apt-mirror-to-create-your-own-ubuntu-mirror/](http://odzangba.wordpress.com/2007/12/24/use-apt-mirror-to-create-your-own-ubuntu-mirror/)
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

The problem is that the whole ubuntu repo is huge! Something about 30 GB. If you can create a local repo on your laptop then you can move the packages you want to the server.

2) To find the (recursive) dependencies of a package I prefer to use

```
apt-rdepends package
apt-rdepends package | grep NotInstalled
```

3) To get proper links use

```
apt-get --print-uris --yes install <Package> | grep ^\' | cut -d\' -f2 > list.htm
```

and grab them using wget:

```
wget --input-file list.htm
```

(See [https://help.ubuntu.com/community/AptGet/Offline/PrintUris](https://help.ubuntu.com/community/AptGet/Offline/PrintUris))

4) To list all installed packages use

```
dpkg --get-selections
dpkg --get-selections > list.txt
```

I don't know how you can list all uninstalled packages.

---

