---
title: "Major Problems with kubuntu"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by xanrer on 2009-08-17
I'm having a major problems installing things with kubuntu, for example, when I try to install wine I run the following commands;

sudo apt-get update will bring this;

```
Hit http://www.nic.funet.fi jaunty Release.gpg
Ign http://www.nic.funet.fi jaunty/main Translation-en_US
Ign http://www.nic.funet.fi jaunty/restricted Translation-en_US
Ign http://www.nic.funet.fi jaunty/universe Translation-en_US  
Ign http://www.nic.funet.fi jaunty/multiverse Translation-en_US
Hit http://www.nic.funet.fi jaunty-updates Release.gpg         
Ign http://www.nic.funet.fi jaunty-updates/main Translation-en_US
Ign http://www.nic.funet.fi jaunty-updates/restricted Translation-en_US
Ign http://www.nic.funet.fi jaunty-updates/universe Translation-en_US  
Ign http://www.nic.funet.fi jaunty-updates/multiverse Translation-en_US
Hit http://www.nic.funet.fi jaunty-security Release.gpg                
Ign http://www.nic.funet.fi jaunty-security/main Translation-en_US     
Ign http://www.nic.funet.fi jaunty-security/restricted Translation-en_US
Ign http://www.nic.funet.fi jaunty-security/universe Translation-en_US  
Ign http://www.nic.funet.fi jaunty-security/multiverse Translation-en_US
Hit http://www.nic.funet.fi jaunty Release                              
Hit http://www.nic.funet.fi jaunty-updates Release                      
Hit http://www.nic.funet.fi jaunty-security Release                     
Get:1 http://www.nic.funet.fi jaunty/main Packages [1251kB]             
99% [1 Packages bzip2 0]                                                
bzip2: Data integrity error when decompressing.                         
        Input file = (stdin), output file = (stdout)                    

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty/main Packages
  Sub-process bzip2 returned an error code (2)  
Hit http://www.nic.funet.fi jaunty/restricted Packages
Get:2 http://www.nic.funet.fi jaunty/main Sources [555kB]
Hit http://www.nic.funet.fi jaunty/restricted Sources    
Get:3 http://www.nic.funet.fi jaunty/universe Packages [4732kB]
27% [2 Sources bzip2 0] [3 Packages 0/4732kB 0%]               
bzip2: Data integrity error when decompressing.                
        Input file = (stdin), output file = (stdout)           

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty/main Sources 
  Sub-process bzip2 returned an error code (2)  
Get:4 http://www.nic.funet.fi jaunty/universe Sources [2375kB]                                                      
73% [3 Packages bzip2 0] [4 Sources 2202/2375kB 0%]                                                       317kB/s 7s
bzip2: Data integrity error when decompressing.                                                                     
        Input file = (stdin), output file = (stdout)                                                                

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty/universe Packages                                                                
  Sub-process bzip2 returned an error code (2)                                                                      
Get:5 http://www.nic.funet.fi jaunty/multiverse Packages [189kB]                                                    
97% [4 Sources bzip2 0] [5 Packages 0/189kB 0%]                                                           285kB/s 0s
bzip2: Data integrity error when decompressing.                                                                     
        Input file = (stdin), output file = (stdout)                                                                

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty/universe Sources                                                                 
  Sub-process bzip2 returned an error code (2)                                                                      
Get:6 http://www.nic.funet.fi jaunty/multiverse Sources [107kB]                                                     
98% [5 Packages bzip2 0] [6 Sources 0/107kB 0%]                                                           285kB/s 0s
bzip2: Data integrity error when decompressing.                                                                     
        Input file = (stdin), output file = (stdout)                                                                

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty/multiverse Packages                                                              
  Sub-process bzip2 returned an error code (2)                                                                      
Get:7 http://www.nic.funet.fi jaunty-updates/main Packages [133kB]                                                  
98% [6 Sources bzip2 0] [7 Packages 0/133kB 0%]                                                           285kB/s 0s
bzip2: Data integrity error when decompressing.                                                                     
        Input file = (stdin), output file = (stdout)                                                                

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty/multiverse Sources                                                               
  Sub-process bzip2 returned an error code (2)                                                                      
Hit http://www.nic.funet.fi jaunty-updates/restricted Packages                                                      
Get:8 http://www.nic.funet.fi jaunty-updates/main Sources [41.2kB]                                                  
99% [7 Packages bzip2 159744] [8 Sources 18824/41.2kB 45%]                                                285kB/s 0s
bzip2: Data integrity error when decompressing.                                                                     
        Input file = (stdin), output file = (stdout)                                                                

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty-updates/main Packages                                                            
  Sub-process bzip2 returned an error code (2)                                                                      
Hit http://www.nic.funet.fi jaunty-updates/restricted Sources                                                       
Get:9 http://www.nic.funet.fi jaunty-updates/universe Packages [45.3kB]                                             
99% [9 Packages bzip2 0] [Connecting to www.nic.funet.fi (193.166.3.3)]                                   285kB/s 0s
bzip2: Data integrity error when decompressing.                                                                     
        Input file = (stdin), output file = (stdout)                                                                

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty-updates/universe Packages                                                        
  Sub-process bzip2 returned an error code (2)                                                                      
Hit http://www.nic.funet.fi jaunty-updates/universe Sources                                                         
Hit http://www.nic.funet.fi jaunty-updates/multiverse Packages                                                      
Hit http://www.nic.funet.fi jaunty-updates/multiverse Sources                                                       
Get:10 http://www.nic.funet.fi jaunty-security/main Packages [68.8kB]                                               
Hit http://www.nic.funet.fi jaunty-security/restricted Packages                                                     
Hit http://www.nic.funet.fi jaunty-security/main Sources                                                            
Hit http://www.nic.funet.fi jaunty-security/restricted Sources                                                      
Hit http://www.nic.funet.fi jaunty-security/universe Packages                                                       
Hit http://www.nic.funet.fi jaunty-security/universe Sources                                                        
Hit http://www.nic.funet.fi jaunty-security/multiverse Packages                                                     
Hit http://www.nic.funet.fi jaunty-security/multiverse Sources                                                      
99% [10 Packages bzip2 0]                                                                                 285kB/s 0s
bzip2: Data integrity error when decompressing.                                                                     
        Input file = (stdin), output file = (stdout)                                                                

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://www.nic.funet.fi jaunty-security/main Packages                                                           
  Sub-process bzip2 returned an error code (2)                                                                      
Fetched 9497kB in 27s (351kB/s)                                                                                     
W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty/main/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty/universe/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty/multiverse/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty/multiverse/source/Sources.bz2 Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty-updates/main/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty-updates/universe/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/jaunty-security/main/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I've tried to change the server where it downloads from, but it gives the same errors for the same files. 

And when I run sudo apt-get install wine;

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

```
The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
        Depends: lib32nss-mdns (>= 0.10-3) but it is not installable
        Recommends: ttf-liberation but it is not installable
        Recommends: winbind but it is not installable
        Recommends: ttf-mscorefonts-installer but it is not installable
E: Broken packages
```

Ok, broken dependencies, fine, I'll fix that. 

I go into the KpackageKit, search for wine, and click the "apply now" button to install it, a window that shows "querying" comes up, and now it has been up there for 45 mins now, I don't think it will do anything good.

I've used apt-get -f install and autoclean, it doesn't work anyway.

So the big question is; How do I fix my broken dependencies without updating?

Thanks in advance!

PS: Got 9.04


EDIT: Tried to Install with the GUI, but it ended when I tried to install with KPackageKit, it gave me this;

```
A problem that we were not expecting has occurred.
Please report this bug with the error description.

----

Traceback (most recent call last): File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run threading.Thread.run(self) File "/usr/lib/python2.6/threading.py", line 477, in run self.__target(*self.__args, **self.__kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 168, in wrapper func(*args, **kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1261, in doInstallFiles deb = debfile.DebPackage(path, self._cache) File "/usr/lib/packagekit/debfile.py", line 53, in __init__ self.open(filename) File "/usr/lib/packagekit/debfile.py", line 60, in open control = apt_inst.debExtractControl(open(self.filename)) SystemError: E:Tar checksum failed, archive corrupted 
```

---

