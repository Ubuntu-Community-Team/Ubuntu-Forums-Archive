---
title: "Acer 4830tg with Ubuntu 11.10. CUDA, Optimus,sound,  temperatures,noise questions"
date: 2012-02-02
forum: Hardware
---

### Post by pasoleatis on 2012-02-02
Hello,

I have recently bought an acer 4830tg with this configuration:
cpu i7 2620m, 8GB DDR3, 160 GB SSD, gpu intel integrated and nvidia 540m. 

I installed Ubuntu 11.10. I can happily report that it works almost everything. DVD RW works, bluetooth works, wireless works

Though I have a few problems.

First question is related temperatures and ventilator noise. I read several posts about the cooling system. It appears that the nvdiai card and cpu share the same heat sink. This is causing the cpu to underclock when nvidia card is used intensively, because of the heat . Some people suggested to 'improve' de design by putting extra small sinks on top of the other. my problem is I was not able to remove the panel. A guide to how to open back panel would be very useful.

Second question is about the optimus. I only need nvidia when I am doing cuda programming. I made the mistake to install the drivers suggested by ubuntu. Where can I find a guide about how to uninstall those and install the optimus support. I am ok to do everything on he integrated gpu expect the cuda. The battery life is also halved now without the optimus support. What happens when Ubuntu makes a kernel update will it require to install again the optimus support and the nvidia driver? Please share about optimus even if you have other laptops the problem is similar on many laptops.

Third is question is how to get the microfon to work. At this moment I was not able to do a skype call.

---

### Post by MoreOrLess on 2012-02-02
For the microphone, can you post link to alsa info? [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by pasoleatis on 2012-02-02
> **MoreOrLess said:**
> For the microphone, can you post link to alsa info? [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Done. It appears the problem is only in skype, in the testing program the mic works.

---

### Post by pasoleatis on 2012-02-03
I managed to get the optimus running. Unfortunately I only get up to 5 hours of battery. 
CUDA works as well. After a few installations and playing around managed to make it work.

> 
I have  Acer 4830tg with nvidia 540m. I managed as well to get cuda  working. Following the original poster. I did the following. First  install the latest version of bumblebee and check it is working. Next I  installed the 4.4 compiler. I did not uninstall the 4.6 compiler because  it results in uninstalling bumblebee. I made links gcc --> gcc-4.4  and and g++ --> g++-4.4. I followed the other step which are require  to install cuda on ubuntu 11.10 and installed all the other stuff  required. At the end I installed the nvidia developer driver ( I got  errors like device not supported, but I just passed over).  At the end I  did not update the X configuration files. Now install the cudatoolkit  and compile the examples. Run the cuda programs with optirun. 

I had to reinstall 4 time ubuntu today (lucky me i have an ssd) because I  messed up the nvidia driver installation and the compilers. the latest  version of bumblebee si somehow linked to gcc-4.6. removing gcc-4.6 will  uninstall the bumblebee. So I kept it and install aside the 4.4  versions and used symbolic links to those. The commands gcc -v and g++  -v should give 4.4 in order to compile cuda programs. 

For  bumblebee follow this tutorial: [http://www.ivegotavi...weed-on-ubuntu/]("http://www.ivegotavirus.com/blog/2012/01/23/installing-bumblebee-3-0-tumbleweed-on-ubuntu/") . Some instructions about installing cuda I took from here: [http://blog.ryant.or...buntu-1110.html]("http://blog.ryant.org/2011/12/installing-cuda-toolkit-on-ubuntu-1110.html") .                                                  

[http://forums.nvidia.com/index.php?showtopic=208065](http://forums.nvidia.com/index.php?showtopic=208065)


---

