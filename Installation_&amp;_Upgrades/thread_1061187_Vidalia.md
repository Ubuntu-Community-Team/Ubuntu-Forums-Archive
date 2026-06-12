---
title: "Vidalia"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by ultimate_aektzis on 2009-02-05
Hi,
I have just installed vidalia project by compiling its source code but I can't find it on the applications menu or find the command that executes it from a console command.Any ideas?

Thanks in advance.

---

### Post by Partyboi2 on 2009-02-05
Try typing vidalia in a terminal.

---

### Post by ultimate_aektzis on 2009-02-06
> **Partyboi2 said:**
> Try typing vidalia in a terminal.

I have already tried it before posting;)

---

### Post by Partyboi2 on 2009-02-06
ok then try
```
/path/to/build/src/vidalia/
```So if vidalia was located in your /home directory you would use
```
/home/user/vidalia-0.1.10/build/src/vidalia
``` *Replace user with correct name.

---

### Post by ultimate_aektzis on 2009-02-06
There is no folder name build:(

From console ls

> CHANGELOG            config.h                 doc            LICENSE-LGPLV3
cmake                config.h.in              HACKING        LICENSE-OPENSSL
CMakeCache.txt       contrib                  INSTALL        Makefile
CMakeFiles           CPackConfig.cmake        LICENSE        pkg
cmake_install.cmake  CPackSourceConfig.cmake  LICENSE-GPLV2  README
CMakeLists.txt       CREDITS                  LICENSE-GPLV3  src


---

### Post by Partyboi2 on 2009-02-06
I am not sure what steps you took to compile it, but the steps I took were the steps listed in the INSTALL file and I was able to successfully start the program with the above command I posted.

---

### Post by ultimate_aektzis on 2009-02-06
I followoed the steps from the site.And I think that there arent any .deb's somewhere on the interent or in the repos:(

---

### Post by Partyboi2 on 2009-02-06
Ok if you finished compiling with 'sudo make install' it would have installed  to
```
/usr/local/bin/
```so try
```
/usr/local/bin/vidalia
```

---

### Post by ultimate_aektzis on 2009-02-06
I didnt make sudo make install.The instructions on the site said to dodo ```
cmake . && make
```

---

### Post by Partyboi2 on 2009-02-06
You should be able to enter the vidalia-0.1.10 directory and use the ls command and it should list a src folder. If there is no /src folder then I would suggest remaining in the  vidalia-0.1.10 directory and try recompiling using the /build directory way
```
mkdir build
cd build
cmake ..
make
sudo make install
```
then start with
```
/usr/local/bin/vidalia
```
When you run those commands make sure that they finish without errors or complaining about missing packages.

---

### Post by ultimate_aektzis on 2009-02-06
Thanks for help partyboi.I will try it.:D

---

### Post by 1nfinitel00p on 2009-05-13
> **Partyboi2 said:**
> Try typing vidalia in a terminal.

hey Partyboi, I wanted to ask you as a Jaunty user, did you already install vidalia for your version?

I found that there's still no support for Jaunty because Vidalia delays 1 month or so posting the new version is that true?

I already installed libevent
and vidalia

everything went right, but when I start Vidalia in  it automatically open de GUI and says  p, li { white-space: pre-wrap; }  Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified.


then I enter to settings but I dont know which executable tor file I tried with /tor-0.2.0.22-rc/contrib/tor.sh but nothing

so Im not sure of the correct path of the file, probably you know this. Thanks!

---

### Post by husunzi on 2009-11-11
Tor is still not available in the repositories for Karmic (9.10), although Vidalia is, but I'm still getting the same "Vidalia was unable to start Tor" message. Either the Vidalia in the repositories doesn't include Tor (strange, since Tor is the central component), or there's another problem. I had tried [this Jaunty fix]("http://ubuntuforums.org/showpost.php?p=7832839&postcount=10") before, but it still didn't work (after it apparently installed, Vidalia continued to say "unable to start Tor), same as several other people on these threads. Any suggestions? Will Tor or a working Vidalia ever be returned to the Ubuntu repositories? This is essential for people living in countries where important websites are blocked (regular proxies don't work for a lot of things).

---

### Post by shadowlands on 2009-11-23
look in applications and click the Internet app and you should see it on that list of programs you have for the internet.

---

