---
title: "g++ install problem"
date: 2008-10-21
forum: General Help
---

### Post by Spitphire on 2008-10-21
trying to install g++, here's what I'm getting, any ideas?

```

(~)lb $ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: g++-4.2 (>= 4.2.3-1) but it is not going to be installed
E: Broken packages


```

```

(~)lb $ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release                                 
Hit http://archive.ubuntu.com hardy Release                                    
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://archive.ubuntu.com hardy/main Sources                     
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://archive.canonical.com hardy/partner Sources               
Hit http://archive.ubuntu.com hardy/restricted Sources               
Hit http://us.archive.ubuntu.com hardy/restricted Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Reading package lists... Done


```

---

### Post by jamesrl on 2008-10-21
Could you post the output of 'dpkg -l g++*' to see what g++ you have installed (i'm assuming you have something already installed that is giving you a conflict)?  My output is
```

 $ dpkg -l g++*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                        Version                                     Description
+++-===========================================-===========================================-======================================================================================================
ii  g++                                         4:4.2.3-1ubuntu6                            The GNU C++ compiler
ii  g++-3.3                                     1:3.3.6-15ubuntu6                           The GNU C++ compiler
ii  g++-3.4                                     3.4.6-6ubuntu5                              The GNU C++ compiler
ii  g++-4.1                                     4.1.2-21ubuntu1                             The GNU C++ compiler
un  g++-4.1-multilib                            <none>                                      (no description available)
ii  g++-4.2                                     4.2.3-2ubuntu7                              The GNU C++ compiler
un  g++-4.2-multilib                            <none>                                      (no description available)
un  g++-multilib                                <none>                                      (no description available)



```

---

### Post by Spitphire on 2008-10-22
Well for some reason when I tried it today it seemed to work.  Unsure how that happened.  I made zero changes, maybe one of the repos was down yesterday??

```

(~)lb $ dpkg -l g++*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  g++            4:4.2.3-1ubunt The GNU C++ compiler
ii  g++-4.2        4.2.3-2ubuntu7 The GNU C++ compiler
un  g++-4.2-multil <none>         (no description available)
un  g++-multilib   <none>         (no description available)


```

---

### Post by Sycron on 2008-10-22
You can try ```
sudo aptitude install g++
```.

---

### Post by jespdj on 2008-10-22
Note that if you want to compile C++ programs, you would normally need to install the package **build-essential**, which besides the bare compiler also installs the necessary header files for the standard C++ library.
```
sudo apt-get install build-essential
```

---

### Post by ajaythomas.inc on 2010-12-12
My problem is i have installed g++ compiler and i m using codeblocks IDE. But it fails to recognize classes etc. This is my output for
~$ dpkg -l g++*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  g++            4:4.4.3-1ubunt The GNU C++ compiler
ii  g++-4.4        4.4.3-4ubuntu5 The GNU C++ compiler
un  g++-4.4-multil <none>         (no description available)
un  g++-multilib   <none>         (no description available)



> **jamesrl said:**
> Could you post the output of 'dpkg -l g++*' to see what g++ you have installed (i'm assuming you have something already installed that is giving you a conflict)?  My output is
```

 $ dpkg -l g++*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                        Version                                     Description
+++-===========================================-===========================================-======================================================================================================
ii  g++                                         4:4.2.3-1ubuntu6                            The GNU C++ compiler
ii  g++-3.3                                     1:3.3.6-15ubuntu6                           The GNU C++ compiler
ii  g++-3.4                                     3.4.6-6ubuntu5                              The GNU C++ compiler
ii  g++-4.1                                     4.1.2-21ubuntu1                             The GNU C++ compiler
un  g++-4.1-multilib                            <none>                                      (no description available)
ii  g++-4.2                                     4.2.3-2ubuntu7                              The GNU C++ compiler
un  g++-4.2-multilib                            <none>                                      (no description available)
un  g++-multilib                                <none>                                      (no description available)



```

---

### Post by Spyderkid on 2010-12-12
are you using the right code? (this sometimes happens)
```

sudo apt-get install build-essential

```

---

