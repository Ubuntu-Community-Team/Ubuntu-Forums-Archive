---
title: "Radeon 7870 HD GHz Edition not working?"
date: 2015-06-20
forum: Hardware
---

### Post by roy27 on 2015-06-20
I installed the latest drivers, I tried their custom and then their automatic installation (ended up breaking my boot a couple of times, but right now it seems alright). The games won't run, and I think it's because of the driver because when I had the normal X.Org Driver, they run perfectly.

Name of driver: Advanced Micro Deviced, Inc. [AMD/ATI] Pitcairn XT [Radeon 7870 HD GHz Edition]
option: Using video driver for the AMD graphics accelerators from fglrx, using video driver for the AMD graphics accelerators from fglrx-updates, Using X.Org X server -- AMD/ATI display driver wrapper from xserver-xorg-video-ati (Recommended Driver). 

Right now I am using the X.Org driver (just to be safe) but I am not sure it really matters, I tried selecting each one, and nothing really happens.

I tried launching the AMD Catalyst Control Center (the icon is actually in my Kickoff Application Launcher; two of them actually [one of them is for Admin. access]) but it doesn't work, it gives me an error that's it's not installed (when I have the driver selected in the Driver Manager) and it just tells me it's not there (if I am using the X.Org driver).

```
aki@koipuo:~$ sudo amdcccle
[sudo] password for aki: 
sudo: amdcccle: command not found
aki@koipuo:~$ sudo amdccle 
sudo: amdccle: command not found
aki@koipuo:~$ ^C
aki@koipuo:~$ amdcccle
amdcccle: command not found
aki@koipuo:~$ amdccle
amdccle: command not found
aki@koipuo:~$ sudo amdxdg-su -c amdcccle
sudo: amdxdg-su: command not found
aki@koipuo:~$ amdxdg-su -c amdcccle
amdxdg-su: command not found
aki@koipuo:~$ amdcccle
amdcccle: command not found
aki@koipuo:~$ sudo apt-get update
Ign http://security.ubuntu.com trusty-security InRelease
8% [Waiting for headers] [Connecting to extras.ubuntu.com (91.189.92.152)]                                                                          Ign http://us.archive.ubuntu.com trusty InRelease
14% [Waiting for headers] [Connecting to extras.ubuntu.com (91.189.92.152)                                                                          Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
99% [Waiting for headers] [1 Release.gpg 933 B/933 B 100%] [Waiting for he                                                                          Ign http://us.archive.ubuntu.com trusty-updates InRelease            
Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]   
5% [Waiting for headers] [2 Release 2,439 B/63.5 kB 4%] [Waiting for heade                                                                          Hit http://us.archive.ubuntu.com trusty Release.gpg
22% [2 Release 13.4 kB/63.5 kB 21%] [Waiting for headers] [Waiting for hea                                                                          Get:3 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
47% [3 Release.gpg 933 B/933 B 100%] [2 Release 28.5 kB/63.5 kB 45%] [Wait47% [2 Release 28.5 kB/63.5 kB 45%] [Waiting for headers] [Waiting for hea                                                                          Ign http://extras.ubuntu.com trusty InRelease
47% [Waiting for headers] [2 Release 28.5 kB/63.5 kB 45%] [Waiting for hea                                                                          Hit http://us.archive.ubuntu.com trusty Release
87% [2 Release 54.7 kB/63.5 kB 86%] [Waiting for headers] [Waiting for hea87% [Release gpgv 58.5 kB] [Waiting for headers] [2 Release 54.7 kB/63.5 k100% [Release gpgv 58.5 kB] [Waiting for headers] [Waiting for headers] [W                                                                          Hit http://deb.torproject.org trusty InRelease
                                                                          Get:4 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]    
61% [2 Release gpgv 63.5 kB] [4 Release 13.4 kB/63.5 kB 21%] [Waiting for                                                                           Hit http://extras.ubuntu.com trusty Release.gpg          
61% [InRelease gpgv 3,526 B] [4 Release 13.4 kB/63.5 kB 21%] [Waiting for 75% [4 Release 31.3 kB/63.5 kB 49%] [Waiting for headers] [Waiting for hea                                                                          Get:5 http://security.ubuntu.com trusty-security/main Sources [85.8 kB]
58% [4 Release 58.8 kB/63.5 kB 93%] [5 Sources 0 B/85.8 kB 0%] [Waiting fo                                                                          Hit http://deb.torproject.org trusty/main amd64 Packages
100% [4 Release 63.5 kB/63.5 kB 100%] [5 Sources 84.8 kB/85.8 kB 99%] [Wai                                                                          100% [Packages 5,684 B] [5 Sources 84.8 kB/85.8 kB 99%] [Waiting for heade                                                                          100% [Packages 5,684 B] [4 Release gpgv 63.5 kB] [5 Sources 84.8 kB/85.8 k100% [4 Release gpgv 63.5 kB] [Waiting for headers] [5 Sources 84.8 kB/85.100% [Waiting for headers] [5 Sources 84.8 kB/85.8 kB 99%] [Waiting for he                                                                          Hit http://extras.ubuntu.com trusty Release
100% [Waiting for headers] [5 Sources 84.8 kB/85.8 kB 99%] [Waiting for he100% [Release gpgv 11.9 kB] [Waiting for headers] [5 Sources 84.8 kB/85.8 100% [Waiting for headers] [5 Sources 84.8 kB/85.8 kB 99%] [Waiting for he                                                                          Hit http://us.archive.ubuntu.com trusty/main Sources                  
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [5 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers] [Waiti                                                                          Hit http://deb.torproject.org trusty/main i386 Packages
100% [5 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers] [Waiti100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://us.archive.ubuntu.com trusty/restricted Sources
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Get:6 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
100% [Sources 5,000 kB] [Waiting for headers] [6 Sources 1,032 B/2,061 B 5100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [6 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers] [Waiti100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://us.archive.ubuntu.com trusty/universe Sources
                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse Sources
                                                                          Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
                                                                          Get:7 http://security.ubuntu.com trusty-security/universe Sources [26.2 kB]
                                                                          Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [2,333 B]
                                                                          Hit http://extras.ubuntu.com trusty/main Sources
                                                                          100% [7 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers] [Waiti100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [299 kB]
48% [Sources 5,000 kB] [Waiting for headers] [9 Packages 13.0 kB/299 kB 4%48% [8 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers] [9 Pack55% [Sources 5,000 kB] [Waiting for headers] [9 Packages 50.5 kB/299 kB 17                                                                          Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
55% [Sources 5,000 kB] [Waiting for headers] [9 Packages 50.5 kB/299 kB 1796% [Waiting for headers] [9 Packages 50.5 kB/299 kB 17%] [Waiting for hea96% [Packages 5,680 B] [Waiting for headers] [9 Packages 50.5 kB/299 kB 1796% [Waiting for headers] [9 Packages 50.5 kB/299 kB 17%] [Waiting for hea96% [Sources 22.9 kB] [Waiting for headers] [9 Packages 50.5 kB/299 kB 17%                                                                          Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
96% [Sources 22.9 kB] [9 Packages 101 kB/299 kB 34%] [Waiting for headers]96% [Waiting for headers] [9 Packages 101 kB/299 kB 34%] [Waiting for head96% [Sources 27.9 MB] [Waiting for headers] [9 Packages 101 kB/299 kB 34%]                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
97% [Sources 27.9 MB] [9 Packages 155 kB/299 kB 52%] [Waiting for headers]                                                                          Hit http://extras.ubuntu.com trusty/main amd64 Packages
97% [Sources 27.9 MB] [Waiting for headers] [9 Packages 155 kB/299 kB 52%]                                                                          Hit http://us.archive.ubuntu.com trusty/main i386 Packages
97% [Sources 27.9 MB] [9 Packages 155 kB/299 kB 52%] [Waiting for headers]                                                                          Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
98% [Sources 27.9 MB] [9 Packages 200 kB/299 kB 67%] [Waiting for headers]                                                                          Hit http://extras.ubuntu.com trusty/main i386 Packages
99% [Sources 27.9 MB] [Waiting for headers] [9 Packages 244 kB/299 kB 82%]                                                                          Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
99% [Sources 27.9 MB] [9 Packages 244 kB/299 kB 82%] [Waiting for headers]100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin100% [9 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Waiti                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
100% [9 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Waiti                                                                          Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
100% [9 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [10 Pa100% [9 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Waiti                                                                          Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [109 kB]
98% [9 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [11 Pac99% [Sources 27.9 MB] [Waiting for headers] [11 Packages 76.6 kB/109 kB 71100% [10 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [11 P100% [Sources 27.9 MB] [Waiting for headers] [11 Packages 107 kB/109 kB 98100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin100% [11 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Wait                                                                          Hit http://us.archive.ubuntu.com trusty/main Translation-en
100% [11 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Wait                                                                          Ign http://deb.torproject.org trusty/main Translation-en_US
100% [11 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Wait                                                                          Get:12 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,686 B]
100% [11 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [12 P100% [11 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Wait100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
                                                                          Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
                                                                          Hit http://us.archive.ubuntu.com trusty/universe Translation-en
                                                                          Get:13 http://us.archive.ubuntu.com trusty-updates/main Sources [210 kB]
                                                                          Get:14 http://security.ubuntu.com trusty-security/main i386 Packages [285 kB]
                                                                          Get:15 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
                                                                          Ign http://deb.torproject.org trusty/main Translation-en
                                                                          97% [Sources 27.9 MB] [13 Sources 35.4 kB/210 kB 17%] [Waiting for headers                                                                          97% [12 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 35.4 kB/210 kB 197% [Sources 27.9 MB] [13 Sources 35.4 kB/210 kB 17%] [Waiting for headers97% [14 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 35.4 kB/210 kB 1                                                                          Get:16 http://security.ubuntu.com trusty-security/universe i386 Packages [109 kB]
96% [14 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 80.7 kB/210 kB 399% [14 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 133 kB/210 kB 63                                                                          Get:17 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,841 B]
99% [14 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 133 kB/210 kB 6399% [14 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 133 kB/210 kB 63100% [Sources 27.9 MB] [13 Sources 193 kB/210 kB 92%] [Waiting for headers100% [15 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 193 kB/210 kB 9100% [Sources 27.9 MB] [13 Sources 193 kB/210 kB 92%] [Waiting for headers100% [16 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 193 kB/210 kB 9                                                                          Hit http://security.ubuntu.com trusty-security/main Translation-en
100% [16 Packages bzip2 0 B] [Sources 27.9 MB] [13 Sources 193 kB/210 kB 9100% [16 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Wait                                                                          Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
100% [16 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Wait100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Get:18 http://us.archive.ubuntu.com trusty-updates/restricted Sources [3,433 B]
                                                                          Get:19 http://us.archive.ubuntu.com trusty-updates/universe Sources [121 kB]
                                                                          Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,143 B]
                                                                          Get:21 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [557 kB]
                                                                          Hit http://security.ubuntu.com trusty-security/restricted Translation-en
                                                                          Hit http://security.ubuntu.com trusty-security/universe Translation-en
                                                                          97% [17 Packages bzip2 0 B] [Sources 27.9 MB] [21 Packages 362 kB/557 kB 6                                                                          97% [Sources 27.9 MB] [21 Packages 362 kB/557 kB 65%] [Waiting for headers                                                                          97% [13 Sources bzip2 0 B] [Sources 27.9 MB] [21 Packages 362 kB/557 kB 65                                                                          100% [Sources 27.9 MB] [21 Packages 529 kB/557 kB 95%] [Waiting for header                                                                          100% [18 Sources bzip2 0 B] [Sources 27.9 MB] [21 Packages 529 kB/557 kB 9                                                                          100% [Sources 27.9 MB] [21 Packages 529 kB/557 kB 95%] [Waiting for header                                                                          100% [19 Sources bzip2 0 B] [Sources 27.9 MB] [21 Packages 529 kB/557 kB 9                                                                          100% [20 Sources bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Waiti                                                                          100% [21 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers] [Wait                                                                          Get:22 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11.8 kB]
100% [21 Packages bzip2 0 B] [Sources 27.9 MB] [22 Packages 2,419 B/11.8 k                                                                          Get:23 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [290 kB]
97% [21 Packages bzip2 0 B] [Sources 27.9 MB] [23 Packages 82.1 kB/290 kB                                                                           Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
100% [21 Packages bzip2 0 B] [Sources 27.9 MB] [24 Packages 2,419 B/12.0 k                                                                          Get:25 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [543 kB]
94% [Sources 27.9 MB] [25 Packages 103 kB/543 kB 19%] [Waiting for headers                                                                          94% [22 Packages bzip2 0 B] [Sources 27.9 MB] [25 Packages 103 kB/543 kB 1                                                                          95% [Sources 27.9 MB] [25 Packages 166 kB/543 kB 31%] [Waiting for headers                                                                          95% [23 Packages bzip2 0 B] [Sources 27.9 MB] [25 Packages 169 kB/543 kB 3                                                                          Ign http://extras.ubuntu.com trusty/main Translation-en_US
                                                                          96% [23 Packages bzip2 0 B] [Sources 27.9 MB] [25 Packages 202 kB/543 kB 3                                                                          99% [Sources 27.9 MB] [25 Packages 490 kB/543 kB 90%] [Waiting for headers                                                                          99% [24 Packages bzip2 0 B] [Sources 27.9 MB] [25 Packages 490 kB/543 kB 9                                                                          Ign http://extras.ubuntu.com trusty/main Translation-en
                                                                          99% [24 Packages bzip2 0 B] [Sources 27.9 MB] [25 Packages 490 kB/543 kB 9                                                                          Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [11.8 kB]
100% [25 Packages bzip2 0 B] [Sources 27.9 MB] [26 Packages 0 B/11.8 kB 0%                                                                          Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [291 kB]
99% [25 Packages bzip2 0 B] [Sources 711 kB] [27 Packages 2,417 B/291 kB 1                                                                          99% [25 Packages bzip2 0 B] [Packages 8,235 kB] [27 Packages 104 kB/291 kB                                                                          Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US       
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 3,139 kB in 5s (584 kB/s)            
Reading package lists... Done
aki@koipuo:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
14% [Connecting to extras.ubuntu.com (91.189.92.152)] [Waiting for headers                                                                          Hit http://deb.torproject.org trusty InRelease
                                                                          25% [Waiting for headers] [Waiting for headers] [Connecting to extras.ubun                                                                          Ign http://us.archive.ubuntu.com trusty-updates InRelease
                                                                          Hit http://security.ubuntu.com trusty-security Release.gpg
                                                                          40% [InRelease gpgv 3,526 B] [Waiting for headers] [Waiting for headers] [                                                                          Hit http://security.ubuntu.com trusty-security Release               
Hit http://us.archive.ubuntu.com trusty Release.gpg                  
Hit http://deb.torproject.org trusty/main amd64 Packages              
23% [Packages 5,684 B] [Waiting for headers] [Waiting for headers] [Waitin100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa                                                                          Hit http://us.archive.ubuntu.com trusty-updates Release.gpg
                                                                          Hit http://security.ubuntu.com trusty-security/main Sources           
100% [Sources 427 kB] [Waiting for headers] [Waiting for headers] [Waiting                                                                          Ign http://extras.ubuntu.com trusty InRelease
100% [Sources 427 kB] [Waiting for headers] [Waiting for headers] [Waiting100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa                                                                          Hit http://us.archive.ubuntu.com trusty Release
                                                                          100% [Release gpgv 58.5 kB] [Waiting for headers] [Waiting for headers] [W100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa                                                                          Hit http://deb.torproject.org trusty/main i386 Packages
                                                                          100% [Packages 5,680 B] [Waiting for headers] [Waiting for headers] [Waiti100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa                                                                          Hit http://security.ubuntu.com trusty-security/restricted Sources
                                                                          100% [Sources 8,902 B] [Waiting for headers] [Waiting for headers] [Waitin100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa                                                                          Hit http://us.archive.ubuntu.com trusty-updates Release
                                                                          100% [Release gpgv 63.5 kB] [Waiting for headers] [Waiting for headers] [W100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa                                                                          Hit http://security.ubuntu.com trusty-security/universe Sources
                                                                          100% [Sources 106 kB] [Waiting for headers] [Waiting for headers] [Waiting100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa                                                                          Hit http://us.archive.ubuntu.com trusty/main Sources
                                                                          100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://security.ubuntu.com trusty-security/multiverse Sources
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://extras.ubuntu.com trusty Release.gpg
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://us.archive.ubuntu.com trusty/restricted Sources
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://security.ubuntu.com trusty-security/main amd64 Packages
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://us.archive.ubuntu.com trusty/universe Sources
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse Sources
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti                                                                          Hit http://extras.ubuntu.com trusty Release
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers] [Waiti100% [Sources 5,000 kB] [Release gpgv 11.9 kB] [Waiting for headers] [Wait100% [Release gpgv 11.9 kB] [Waiting for headers] [Waiting for headers] [W100% [Sources 5,864 B] [Release gpgv 11.9 kB] [Waiting for headers] [Waiti100% [Release gpgv 11.9 kB] [Waiting for headers] [Waiting for headers] [W100% [Sources 22.9 kB] [Release gpgv 11.9 kB] [Waiting for headers] [Waiti100% [Release gpgv 11.9 kB] [Waiting for headers] [Waiting for headers] [W100% [Packages 1,984 kB] [Release gpgv 11.9 kB] [Waiting for headers] [Wai100% [Packages 1,984 kB] [Waiting for headers] [Waiting for headers] [Wait                                                                          Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
100% [Packages 1,984 kB] [Waiting for headers] [Waiting for headers] [Wait                                                                          Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
100% [Packages 1,984 kB] [Waiting for headers] [Waiting for headers] [Wait100% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wa100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/main i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://extras.ubuntu.com trusty/main Sources
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/universe i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/main i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://extras.ubuntu.com trusty/main amd64 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/main Translation-en
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Ign http://deb.torproject.org trusty/main Translation-en_US
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/restricted Translation-en
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://extras.ubuntu.com trusty/main i386 Packages
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Ign http://deb.torproject.org trusty/main Translation-en
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://us.archive.ubuntu.com trusty/main Translation-en
100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers] [Waitin                                                                          Hit http://security.ubuntu.com trusty-security/universe Translation-en
                                                                          Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en 
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en 
Hit http://us.archive.ubuntu.com trusty/universe Translation-en   
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources  
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done                
aki@koipuo:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 fglrx-updates : Depends: fglrx-updates-core but it is not installed
E: Unmet dependencies. Try using -f.
aki@koipuo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx-updates-core
The following NEW packages will be installed:
  fglrx-updates-core
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/72.1 MB of archives.
After this operation, 297 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 203839 files and directories currently installed.)
Preparing to unpack .../fglrx-updates-core_2%3a15.200-0ubuntu0.3_amd64.deb ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the AMD driver
 is not installed, the AMD driver is only partially installed,
 or the current AMD driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing archive /var/cache/apt/archives/fglrx-updates-core_2%3a15.200-0ubuntu0.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx-updates-core_2%3a15.200-0ubuntu0.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
aki@koipuo:~$ sudo apt-get upgrade   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not installed
E: Unmet dependencies. Try using -f.
aki@koipuo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx-core
The following NEW packages will be installed:
  fglrx-core
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/72.2 MB of archives.
After this operation, 297 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 203838 files and directories currently installed.)
Preparing to unpack .../fglrx-core_2%3a15.200-0ubuntu0.3_amd64.deb ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the AMD driver
 is not installed, the AMD driver is only partially installed,
 or the current AMD driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing archive /var/cache/apt/archives/fglrx-core_2%3a15.200-0ubuntu0.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
aki@koipuo:~$ sudo apt-get upgrade   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aki@koipuo:~$ sudo apt-get upgrade   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aki@koipuo:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lib32gcc1 libc6-i386
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 10.0 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 203670 files and directories currently installed.)
Removing lib32gcc1 (1:4.9.1-0ubuntu1) ...
Removing libc6-i386 (2.19-0ubuntu6.6) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libOpenCL.so.1 is not a symbolic link

aki@koipuo:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port E)
00:11.0 RAID bus controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [RAID5 mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
aki@koipuo:~$ ^C
aki@koipuo:~$ 

```

---

