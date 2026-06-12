---
title: "ldconfig deffered processing now taking place"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by limanoit on 2009-04-08
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


guys. 
 i got this error while installing gstreamer plugin for my decoder.. 
what does  ldconfig mean ? 

i tried re installing libc6. and re install everything .  
any clue ? thanks

---

### Post by lloyd_b on 2009-04-08
> **limanoit said:**
> Processing triggers for libc6 ...
ldconfig deferred processing now taking place


guys. 
 i got this error while installing gstreamer plugin for my decoder.. 
what does  ldconfig mean ? 

i tried re installing libc6. and re install everything .  
any clue ? thanks
This is NOT an error.  "ldconfig" is the configuration for the shared library system.  I believe that the "deferred processing" is something that's triggered by the install of certain packages, but which is not handled immediately for some reason.

In short - don't panic.  There's nothing wrong.

Lloyd B.

---

### Post by bapoumba on 2009-04-08
> **limanoit said:**
> Processing triggers for libc6 ...
ldconfig deferred processing now taking place


guys. 
 i got this error while installing gstreamer plugin for my decoder.. 
what does  ldconfig mean ? 

i tried re installing libc6. and re install everything .  
any clue ? thanks
This is not an error, or did you have other output?

[http://linux.die.net/man/8/ldconfig](http://linux.die.net/man/8/ldconfig)
All the library config processes are deferred to the end of install rather than every time a package is installed when you have multiple updates for ex (saves time and bandwidth).
I cannot seem to find the ubuntu-devel thread that changed the behavior, that was several releases ago.

---

### Post by limanoit on 2009-04-08
yah . i was googling and they said its  not an error however the decoder that i am installing is not found yet. this  is gstreamer mpeg 4 decoder that i am installing :(

---

### Post by bapoumba on 2009-04-08
> **limanoit said:**
> the decoder that i am installing is not found yet. this  is gstreamer mpeg 4 decoder that i am installing :(
I'm not sure I understand. Which ubuntu release are you running, and which package are you trying to install? Please post the error to
```
sudo apt-get install <your package name here>
```
may be you do not have all the repositories enabled ?

---

### Post by limanoit on 2009-04-08
hahah btw. do you enable all other repositories that by default is not enabled by ubuntu? 

i usually find the actual file off the internet and install myself . if I have all others repositories that would be helpful.. isnt it? 

thanks..

---

