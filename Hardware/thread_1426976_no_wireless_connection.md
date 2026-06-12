---
title: "no wireless connection"
date: 2010-03-10
forum: Hardware
---

### Post by Paulsandy on 2010-03-10
My laptop is a Toshiba Satallite L450, new, and I decided to run Ubuntu on it, which is new to me. A friend helped me to obtain and install a driver, which is in my Desktop, namely:- rtl8192se_linux_2.6.0010.1012.2009.tar.gz

Twice I have allowed updates (last week 200-something, the other day 19) and each time it kicked out my driver.  So, I have two questions: 

1.  Are there certain updates that I should not allow if I want my wireless to keep working?

and

2.  Is there something that I now need to change in the following instructions, given the updates?  (I have to type this by hand......so, hopefully no typos)  After the first time the following instructions got my wireless back, but this time it is not working.

 sudo apt-get install build-essential
password
cd ~/Desktop
sudo tar -xvzf rtl8192se_liux_2.6.0010.1012.2009_64bit.tar.gz
cd rtl8192se_liux_2.60010.1020.2009_64bit
sudo su
make
make install
exit
sudo reboot



 I can't get past step four (sudo tar -xvzf....and so on....) it says:  

tar: rtl8192se_liux_2.6.0010.1012.2009_64bit.tar.gz: Cannot open: No such file or directory
tar: error is not recoverable: exiting now
tar: Child returned status 2
tar: exiting with failure status due to previous errors


(Don't let my copying out code fool you into thinking I know what I'm doing :p)  Why won't it work this time??  Will updates always kick out my driver??

---

### Post by Paulsandy on 2010-03-12
I copied my problem over in the 'wireless' part of the forum, and the problem was solved by someone kindly and correctly suggesting that I typed the name of the driver incorrectly.

(As I said over on the wireless post: sorry for double posting; I am new and don't know how to delete a post, hence also this added note)

---

