---
title: "FIJI XEROX DocuPrint C525-a Installation Guide (16.04) using alien"
date: 2016-04-20
forum: Hardware
---

### Post by milliganimals on 2016-04-20
These are the steps I followed for successful network printing to the FX DocuPrint C525-a-ap from Ubuntu MATE 64 bit. Should work on all, even older, versions of Ubuntu, and possibly other FX drivers.

1. Locate the correct driver from the Fuji Xerox site [http://fujixerox.com](http://fujixerox.com) (I used the Australian site). 

Or open terminal (Ctrl + Alt + T)

```
cd Downloads 
```

```
wget http://www.fujixeroxprinters.com/downloads/uploaded/dpc525a_linux_.0.0.tar_81c2.zip
```

2. Extract zip file where ever you want it

To extract to current directory

```
unzip dpc525a_linux_.0.0.tar_81c2.zip
```

3. Open extracted folder 
```
cd C525A_LinuxE
```

Should contain file "Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm" which is the 32bit version of the driver for Red Hat or derivatives. To check 
```
ls
```

4. Install alien package using apt-get (skip to 5 if already installed). Alien will be used to convert the rpm package to a deb (Ubuntu/Debian) package and allow installation across architectures.

```
sudo apt-get install alien
```

5. Convert rpm to deb. Make sure you working directory contains the rpm package.

```
sudo alien Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm --scripts --target=all


```

6. Install the newly created file "fuji-xerox-docuprint-c525-a-ap_1.0-2_all.deb" using your preferred method.

```
sudo dpkg -i fuji-xerox-docuprint-c525-a-ap_1.0-2_all.deb
```

7. I finished configuring the printer using the printer utility.

```
system-config-printer
```

---

