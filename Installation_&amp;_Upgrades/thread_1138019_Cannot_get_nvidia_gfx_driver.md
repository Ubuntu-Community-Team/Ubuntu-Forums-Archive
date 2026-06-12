---
title: "Cannot get nvidia gfx driver"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by GuiGuy on 2009-04-26
After the 9.04 upgrade on my wife's PC (i386, nvidia 6600GT) I am unable to install the nvidia driver.

Using the System > Hardware Drivers interface the applet goes to the download progress dialog and stays on 0%. It never commences so after a while all I can do is cancel.

Using envyng -t > 1 > 0 I get the following

> 
Please select the number corresponding to the desired driver and press ENTER   
(or type another number and press Enter to go back to the previous menu):      
0                                                                              

Dowloading the packages...
[===========>                       15.8%                                      ]result could not be parsed                                                                
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: an integer is required                                                    
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
Error in function pulse                                                              
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse  
    self.newObject.updateUi(percent)                                                 
  File "interface.py", line 65, in updateUi                                          
    numHashes = int(round(numHashes))                                                
TypeError: function takes at least one argument                                      
^CError in function stop                                                             
Traceback (most recent call last):                                                   
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 47, in stop   
    def stop(self):                                                                  
KeyboardInterrupt                                                                    
Traceback (most recent call last):                                                   
  File "interface.py", line 432, in <module>                                         
    a.mainMenu()                                                                     
  File "interface.py", line 295, in mainMenu                                         
    a.driverMenu('nvidia')                                                           
  File "interface.py", line 333, in driverMenu                                       
    self.process(self.abstract.install, package)                                     
  File "interface.py", line 391, in process                                          
    myFunction(myArgs)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 206, in install
    self.cacheUi.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText))
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 274, in commit
    res = self._fetchArchives(fetcher, pm)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 205, in _fetchArchives
    return self._runFetcher(fetcher)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 167, in _runFetcher
    res = fetcher.Run()
SystemError: E:Method cdrom has died unexpectedly!


Can anyone explain what I am up against here?

Thanks

---

### Post by apparle on 2009-04-26
I am not much of an expert but his is what happened in my friends PC.
In live Cd the restricted driver manager displayed the card but after installation on the box. It said no proprietary drivers are requred.

I went to Kpacakgekit and saw that there were 4 pacakges 

nvidia-glx-180.........I selected this
nvidia-glx-96
nvidia-glx-173
nvidia-glx-71

Open the package details and just check which one of the above package has your graphic card listed.....also if your package is listed in 180 and others also, install the 180 package.
You can install it from kpacakgekit or from konsole or from p.u.c
After installation just goto restricted drivers manager and activate it. It will directly get activated

---

### Post by Sub101 on 2009-04-26
[http://ubuntuforums.org/showthread.php?t=1135329](http://ubuntuforums.org/showthread.php?t=1135329)

This thread had a similar problem. Although i would be suprised if the issue is still heavy server use.

---

### Post by GuiGuy on 2009-04-26
> **apparle said:**
> 
I went to Kpacakgekit and saw that there were 4 pacakges 

nvidia-glx-180.........I selected this
nvidia-glx-96
nvidia-glx-173
nvidia-glx-71


Thanks, but no joy. After purging, when I run do the above the download gets to 51%, hangs for some time, and then the package management systems crashes.

---

### Post by apparle on 2009-04-27
> **GuiGuy said:**
> Thanks, but no joy. After purging, when I run do the above the download gets to 51%, hangs for some time, and then the package management systems crashes.
Do you have enough space??

Better way use the command line utility apt-get.

try using the command 

```
sudo apt-get install <whichever package you selected>
```

If that also doesn't work then goto [http://www.packages.ubuntu.com/](http://www.packages.ubuntu.com/)
apt-get shows you which all packages(dependencies) have to be installed. Download the .deb packages from the site.
Install them and then activate the driver from the restricted driver manager

---

### Post by GuiGuy on 2009-04-27
> **apparle said:**
> Do you have enough space??


Yes. 

> 
Better way use the command line utility apt-get.


Tried that, same thing. Hangs about halfway through the download. 


> 
Install them and then activate the driver from the restricted driver manager

Thanks, but isn't the driver downloaded from the nvidia site?

---

### Post by GuiGuy on 2009-04-27
Cleaned everything out and tried again. At this point I am not prepared to do a manual install from nvidia site, mainly because in the past it has given me more grief than benefit. 

Tried envyng again. I get this:

>  +----------------------------------------------------------------------------+
 | Number | Candidate Version  | Installed Version | Compatible | Recommended |
 |----------------------------------------------------------------------------|
 | 0      | 180.44-0ubuntu1    | -                 | +          | +           |
 |----------------------------------------------------------------------------|
 | 1      | 173.14.16-0ubuntu1 | -                 | +          | -           |
 |----------------------------------------------------------------------------|
 | 2      | 96.43.10-0ubuntu1  | -                 | +          | -           |
 |----------------------------------------------------------------------------|
 | 3      | 71.86.08-0ubuntu1  | -                 | +          | -           |
 +----------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER
(or type another number and press Enter to go back to the previous menu):
0

Dowloading the packages...
[===================================57.1%====>                                 ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required
/usr/bin/envyng: line 4:  3761 Segmentation fault      sudo python interface.py
sand@sandpc:~$

Did
CTRL+C
envyng --uninstall-all
restart

FOOTNOTE: I note that according to synaptic all the nvidia drivers are installed!? Yet I cannot activate them.

Should I remove all the nvidia stuff synaptic lists or is that likely to create an even greater disaster?

---

### Post by apparle on 2009-04-27
> Thanks, but isn't the driver downloaded from the nvidia site?

Get the deb files from [http://packages.ubuntu.com](http://packages.ubuntu.com) It is the site to download the package files same as done automatically by synaptic or apt-get. It is used in case there is some problem with automatic download or you want to download explicitly

Purge the driver package (nvidia-glx-...) already installed and then reinstall the driver package

---

### Post by GuiGuy on 2009-04-27
> **apparle said:**
> 
Purge the driver package (nvidia-glx-...) already installed and then reinstall the driver package

Thanks. I'm at work now but will try the suggestions when I'm home in about 10 hours. 

Cheers

---

### Post by GuiGuy on 2009-04-28
> **apparle said:**
> Purge the driver package (nvidia-glx-...) already installed and then reinstall the driver package

OK, did that. 

When I started re-installing a warning popped up to insert the jaunty distro CDROM (??!!)

A quick look in the sources.list, and sure enough, the CDROM entry was active. 

Disabled it, restarted the install and all seems to have gone well.

Thanks

---

