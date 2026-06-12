---
title: "Upgrades I don't need/want"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by Jim Lewis on 2009-10-06
Is there some way to tell Update Manager that I don't want/need stuff like DST adjustments for Pakistan?  If I simply ignore the notice I get that upgrades are available, the machine keeps hounding me.  

I really only want the "necessary" upgrades/updates.

Thanks.

Jim in western NC USA

---

### Post by masux594 on 2009-10-06
The update manager update all the packages that u have installed in your system.. If u don't want to install the update because you don't need this package, try to uninstall it..

Sysc, A

---

### Post by drs305 on 2009-10-06
> **Jim Lewis said:**
> Is there some way to tell Update Manager that I don't want/need stuff like DST adjustments for Pakistan?  If I simply ignore the notice I get that upgrades are available, the machine keeps hounding me.  

I really only want the "necessary" upgrades/updates.

Thanks.

Jim in western NC USA

You can set options in Software Sources or Synaptic. Settings, Repositories, Updates. 

If you really don't want to be bothered, you can enable only the security updates. Otherwise, you could set the automatic updates to update less frequently so at least you aren't bothered as often.

---

### Post by slakkie on 2009-10-06
orrrr. You google for apt pinning packages

---

### Post by louieb on 2009-10-06
How is the Update Manager going to know which updates you need?  

You can go into Software Sources > Update tab > and un-check everything but security updates. 
or You can  use Synaptic and lock a package to a specific version.

---

### Post by ajgreeny on 2009-10-06
To pin a package version add these lines to  /etc/apt/preferences:

```
Package: name
Pin: version (number from repos)    
Pin-Priority: 1001
```

---

### Post by slakkie on 2009-10-06
> **ajgreeny said:**
> To pin a package version add these lines to  /etc/apt/preferences:

```
Package: name
Pin: version (number from repos)    
Pin-Priority: 1001
```

I have a nice script to do that for you:

```

dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2}' | grep "$1")
        [ $? -ne 0 ] && return
        for i in $pkg
        do
                pkg2pin $i
        done
}
pkg2pin () {
        [ -z "$1" ] && return
        local pkg
        local msg
        msg="$(date +'%Y%m%d:%H%M%S')"
        for pkg in $@
        do
                pkg=$(dpkg -l "$pkg" 2>/dev/null)
                [ $? -ne 0 ] && continue
                pkg=$(echo -e "$pkg" | grep "^ii" |awk '{print $2" "$3}')
                echo -e "$pkg" | awk '{print "Explanation: Added on '$msg' by pkg2pin or dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}'
        done | sudo tee -a /etc/apt/preferences
}

```

Put in your bashrc and have fun.

---

### Post by drs305 on 2009-10-06
> **slakkie said:**
> I have a nice script to do that for you:

Put in your bashrc and have fun.

Karmic now has an /etc/apt/preferences.d folder. Would that change anything in the script?  I didn't find any references to this folder in a quick search.

---

### Post by slakkie on 2009-10-06
> **drs305 said:**
> Karmic now has an /etc/apt/preferences.d folder. Would that change anything in the script?  I didn't find any references to this folder in a quick search.

Ha, only noticed it because you said so. 

It doesn't really change anything. Preferences file is still used. I think it is the same as /etc/apt/sources.list.d where you can put individual file in, in stead of adding stuff to sources.list.

I could change the scripts to add files to preferences.d, but I don't see any changes on Debian Lenny (I use these scripts on both Ubuntu and Debian). Feel free to change the scripts, I won't do it just yet.

I see it will reach Debian as well:
[http://osdir.com/ml/debian-bugs-closed/2009-07/msg03476.html](http://osdir.com/ml/debian-bugs-closed/2009-07/msg03476.html)

I think it is cooler that # are now accepted as comments!

---

### Post by Jim Lewis on 2009-10-06
Thanks all.  I may just go for Security upgrades and see how that works out.

---

