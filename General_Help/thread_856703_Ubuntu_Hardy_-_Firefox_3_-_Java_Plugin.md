---
title: "Ubuntu Hardy - Firefox 3 - Java Plugin"
date: 2008-07-11
forum: General Help
---

### Post by kubug on 2008-07-11
I had quite the time to get the java plug-in to work correctly with Hardy and Firefox 3, so I wanted to quickly share how I got it working. 

I needed java for logmein.com, to remotely control windows computers, and for some java enable websites (gov of canada). 

When I entered into the address bar of Firefox:

```
about:plugins
```

it wouldn't show the java plug even though I installed everything with 

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

So, after some searching, if found this command: (Enter in your terminal)

```
sudo update-alternatives --config xulrunner-1.9-javaplugin.so

```

After entering your password, you will get prompted with something like this:

> There are 2 alternatives which provide `xulrunner-1.9-javaplugin.so'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/gcjwebplugin.so
*         2    /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

Press enter to keep the default[*], or type selection number: 


Select 2, or which ever has "java-6-sun" in it, and press enter.

Now, close firefox and start it back up. Check to see if you got the plug-in now by entering "about:plugins" in the address bar (without quotes).

Hope this helps someone.

---

### Post by snooppreach on 2008-07-30
hey thnx so much man i didnt think i could ever get it to work. Maddd respect :guitar:

---

### Post by ThaRabbit on 2008-08-03
**Alternative:**
Install firefox 3.x and java as mentionned above.

Now:
```
sudo cd /usr/lib/firefox-3.0.1/plugins/
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

This creates a symbolic link to the actual plugin, now simply restart firefox and type:

```
about:plugins
```

This should show the plugin loaded, you will have to rerun this every time java or firefox updates :) (as the folder name where the new plugin is located will change)

And now we wait for a bugfix :P

---

### Post by kubug on 2008-08-05
Thanks for that post.

I don't think we need a bugfix though, since there are simply two versions of java installed. 

Ubuntu ships with OpenJDK, since Sun's Java is not under the GPL (as far as I know). 

All you need to do is tell Firefox to use Sun's Java instead of the OpenJDK.

But supposedly there is a new version of OpenJDK coming with 8.10, which has more compatibility. [http://www.phoronix.com/scan.php?page=news_item&px=NjYzMQ]("http://www.phoronix.com/scan.php?page=news_item&px=NjYzMQ")

---

### Post by marmida on 2008-08-11
I'm running hardy and I don't see the sun-java6-plugin package.  I've just updated my package list.  Is it in a separate repository that's not enabled by default because of license issues?

I also checked to make sure the plugin was in fact not there; there's no "plugin" dir in the path that ThaRabbit pointed out, inside the jvm.

---

### Post by prankst3r on 2008-08-11
> **marmida said:**
> I'm running hardy and I don't see the sun-java6-plugin package.  I've just updated my package list.  Is it in a separate repository that's not enabled by default because of license issues?

I also checked to make sure the plugin was in fact not there; there's no "plugin" dir in the path that ThaRabbit pointed out, inside the jvm.

I'm having this same problem - did something happen to the sun-java6-plugin package?

---

### Post by kubug on 2008-08-11
> **marmida said:**
> I'm running hardy and I don't see the sun-java6-plugin package.  I've just updated my package list.  Is it in a separate repository that's not enabled by default because of license issues?

I also checked to make sure the plugin was in fact not there; there's no "plugin" dir in the path that ThaRabbit pointed out, inside the jvm.

Hi there,

according to this [http://packages.ubuntu.com/hardy/sun-java6-plugin]("http://packages.ubuntu.com/hardy/sun-java6-plugin") it shows that it's part of the multiverse repository. Did you enable that?

If not, follow this direction: [http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html]("http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html")

Cheers!

---

### Post by Qloor on 2008-09-07
Thanks!

---

### Post by karls0 on 2008-09-07
Hi kubug,

I have installed java according to the instructions on [http://www.java.com/de/download/help/5000010500.xml#100]("http://www.java.com/de/download/help/5000010500.xml#100"). The plugin showed up in about:plugins, but without any file-extensions and it didn't work. Therefore I tried Your way of things. Now I see two versions of libjavaplugin_oji.so, both without file-extension - but now java works!

Thanks a lot !!!

---

### Post by NoTownKasper on 2008-11-23
I've got a very similar problem trying to find the sun-java6-plugin. Apparently it has been removed from the repository or something because no matter where I look, it's unavailable. Yes I have multiverse enabled. This is going to be a serious problem since I need access to java for several work related sites...

---

### Post by kubug on 2008-11-23
> **NoTownKasper said:**
> I've got a very similar problem trying to find the sun-java6-plugin. Apparently it has been removed from the repository or something because no matter where I look, it's unavailable. Yes I have multiverse enabled. This is going to be a serious problem since I need access to java for several work related sites...

Are you still using Hardy? Or are you in Intrepid? Are you using 64-bit?

In any case, if you are in Hardy and using the 32-bit, make sure to enable all the repositories (restricted, universe and multiverse). 

If you are using 64-bit you are going to be in trouble. I am now on Intrepid 64-bit and there is no sun-java6-plugin package. From what I know it has to do with that there is only 32-bit packages available.

Here is a link:
[http://ubuntuforums.org/showthread.php?t=986696&highlight=sun-java6-plugin+64]("http://ubuntuforums.org/showthread.php?t=986696&highlight=sun-java6-plugin+64")

Hope that helped.

---

### Post by distortedecho on 2009-08-07
Su-perb!!!!

---

### Post by ottawa on 2009-08-23
> **kubug said:**
> Are you still using Hardy? Or are you in Intrepid? Are you using 64-bit?

In any case, if you are in Hardy and using the 32-bit, make sure to enable all the repositories (restricted, universe and multiverse). 

I am on Hardy 32bit and as of August 23,2009 I am not able to get sun-java6 from the repositories, all activated.

 ```
sudo update-alternatives --config xulrunner-1.9-javaplugin.so
```

gave me

```
 No alternatives for xulrunner-1.9-javaplugin.so.
```

But I got it working through the "backdoor". A linux newbie step. :)

Steps I did:
1. Go to [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) and click the "verify java version" button.
2. as no plugin is installed, FF 3.0 pops up at the top "Missing plugin".
3. Choose install
4. Enter root password to install software
5. Choose Sun Java 6 (not marked as default)
6. Install, accept license and Sun Java 6 is installed 

Finally my webmin filemanager is working. :)

I had to figure this out, as I wanted to use my new ubuntu machine and not relying on the windows machine as it was working there just fine.
Shame on ubuntu. ;)

Happy Ubuntu-ing
Johannes

---

