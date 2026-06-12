---
title: "Xilinx spartan 3e starter kit on Hardy"
date: 2008-11-28
forum: General Help
---

### Post by w.chris on 2008-11-28
If somebody needs to use the starter kit FPGA spartan 3e on Hardy, there are steps to do it:

Install ise (don't install the USB driver cable),

apt-get install libusb-dev
git clone git://git.zerfleddert.de/usb-driver
cd usb-driver
make
make lib32
cp libusb-driver.so /usr/local/lib/
export LD_PRELOAD=/usr/local/lib/libusb-driver.so

That's it. You can now launch Impact from your installation directory.

---

### Post by physeetcosmo on 2009-01-07
Hello,

i am a newbie to Ubuntu. You say to "Install ISE", however i don't know what you mean by that. Install it under Wine? Or is there a command i need to invoke to install the .exe file? i went to the Xilinx Webpack ISE website and clicked "Download the Webpack ISE software free" link and did all that. 

Any help would be appreciated, thanks!

---

### Post by ozancihangir on 2009-01-22
> **physeetcosmo said:**
> Hello,

i am a newbie to Ubuntu. You say to "Install ISE", however i don't know what you mean by that. Install it under Wine? Or is there a command i need to invoke to install the .exe file? i went to the Xilinx Webpack ISE website and clicked "Download the Webpack ISE software free" link and did all that. 

Any help would be appreciated, thanks!


I install it from DVD but it might be the same with internet version. Open a terminal window. Go to xilinx ise directory which includes "setup" file. Type "sudo ./setup" to run setup script. A setup GUI will open. Follow the instructions.

---

### Post by justin8an on 2009-03-23
ok. following the directions above it appears that i am making progress. Impact used to complain about windrvr and it no longer does. However, now when i try to initialize the chain i get "WARNING:IMPACT:923 - Can not find cable, check cable setup!"

I am using ubuntu 8.10 and Xilinx webpack 10.1
I would appreciate any help.
thanks!

---

### Post by iffy2002 on 2009-05-30
I have the same error as [justin8an]("http://ubuntuforums.org/member.php?u=722849")

---

### Post by M1GEO on 2009-08-22
Hey guys.  I have no idea weather this will help you, but I recently got the cable setup to work fine.  I have written it up as it seems to be a working method for me.

Try the method I describe here
[http://www.george-smart.co.uk/wiki/Xilinx_JTAG_Linux](http://www.george-smart.co.uk/wiki/Xilinx_JTAG_Linux)

Best of Luck

George Smart

---

