---
title: "Startup and Random Freeze"
date: 2009-09-29
forum: Hardware
---

### Post by bjunkjoe on 2009-09-29
Hi All,

  	 	 	 	 	 	  I have recently started having a problem with my ubuntu 9.04. It so happen
 

 It so happen that a couple of days back the laptop switched off during a power outage as my battery is out. After this incident I am experiencing the following problems
 

 
[LIST=1]
[*]Ubuntu 9.04 does not start up it 	just hangs.
[*]In recovery mode also it hangs at 	random points. Like file check, or mount or some times at the 	recovery menu after multiple times I will be able to boot up and 	login successfully
[*]Now after login some times it 	freezes and I have to hard boot  	
[*]after successfully login if I try 	to access the my computer or the Network from the place panel the 	total desktop  icons disappears also my desktop right click menu.  	
 	
 	Error when the desktop icons 	disappears   	
[/LIST]
  

 ** (nautilus:5827): WARNING **: Unable to add monitor: Not supported 
  
 (nautilus:5827): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed 
  
 ** (nautilus:5827): WARNING **: Got GFileInfo with NULL name in computer:///, ignoring. This shouldn't happen unless the gvfs backend is broken. 
  
  
  (nautilus:5827): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
 

 What could be the issue. Kindly advice.


Thanks
BJ

---

### Post by c9ops on 2009-09-30
I had the same problem from testing with moblin.

This is how I solved the trouble.  Give it a shot, maybe it will work for you as well.

```
sudo aptitude remove libglib2.0-0 && sudo aptitude install libglib2.0-0
```

This will prompt first for removal and answer no "N" and press enter.  Next you will be prompted for install.  Enter "Y" and let the install begin.  This should roll back libglib2.0 and dependent packages to the current 'ubuntu' versions and enable proper nautilus functionality again.

cheers

---

### Post by AikenDrum on 2009-10-07
Many, Many thanks for this one :)  was going in circles trying to fix it !

Cheers !


> **c9ops said:**
> I had the same problem from testing with moblin.

This is how I solved the trouble.  Give it a shot, maybe it will work for you as well.

```
sudo aptitude remove libglib2.0-0 && sudo aptitude install libglib2.0-0
```

This will prompt first for removal and answer no "N" and press enter.  Next you will be prompted for install.  Enter "Y" and let the install begin.  This should roll back libglib2.0 and dependent packages to the current 'ubuntu' versions and enable proper nautilus functionality again.

cheers

---

### Post by samtux on 2009-10-13
Thanks very much c9ops!!!!

---

