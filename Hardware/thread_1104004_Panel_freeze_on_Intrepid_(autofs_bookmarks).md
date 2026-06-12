---
title: "Panel freeze on Intrepid (autofs bookmarks)"
date: 2009-03-23
forum: Hardware
---

### Post by mad_jack on 2009-03-23
I have an issue where I have a number of automounted NFS filesystems which contain documents of various types. The filesystems are hosted on servers in my office, *but* there is no external access to them from Internet. 

So, when traveling I often have a problem which I think may be to do with the recent documents list in that opening nautilus, or any file open dialogue in OOO etc. freezes the application and panel. I've tried modding the timeout parameters in /etc/auto.master to add --timeout=60 but it makes no difference. My suspicion is that I have a number of bookmarks to nfs located files, which the panel tries to locate and cannot when working remotely.

Do I need to remove the bookmarks?

Any suggestions welcome.

---

### Post by mad_jack on 2009-03-25
> **mad_jack said:**
> I have an issue where I have a number of automounted NFS filesystems which contain documents of various types. The filesystems are hosted on servers in my office, *but* there is no external access to them from Internet. 

So, when traveling I often have a problem which I think may be to do with the recent documents list in that opening nautilus, or any file open dialogue in OOO etc. freezes the application and panel. I've tried modding the timeout parameters in /etc/auto.master to add --timeout=60 but it makes no difference. My suspicion is that I have a number of bookmarks to nfs located files, which the panel tries to locate and cannot when working remotely.

Do I need to remove the bookmarks?

Any suggestions welcome.

From here: [http://docs.sun.com/app/docs/doc/817-5099/general-8?a=view](http://docs.sun.com/app/docs/doc/817-5099/general-8?a=view)

just changed the file location to suit ubuntu intrepid - i.e. 

/usr/share/nautilus/filesystem-attributes.xml

No more timeouts now when working remotely. Maybe this will help someone else one day.

---

### Post by mfgeg on 2009-04-10
I run into the same issue. Panels are freezing after login. So i found this post about bookmarks problem and autofs.

But i cannot find the xml file under...

/usr/share/nautilus/filesystem-attributes.xml

I even tried to create manually the xml in this location, but no success ;(
Do i miss a something on my ubuntu 8.10 system (a package)?
Or is there another work around?

greetz mfgeg

---

