---
title: "need help with megaraid MegaRAID SAS 2108"
date: 2019-01-14
forum: Hardware
---

### Post by zephar123 on 2019-01-14
OS 18.04

I got a hold of a    	 	 	 	   LSI Logic / Symbios Logic MegaRAID SAS 2108 [Liberator] (rev 04)  I run lspci and it detects the card fine. I can configure the card before boot fine and the drives show up. 

Issue is when I try to setup mega raid. So that I can run commands in terminal (example if I needed to rebuild the raid or something.)

I have followed a few of the guides I could find googling, but all seem to end up with the same error.

 when I try to run a status 

Exit Code: 0x00
 ###############################################
                                       
 
 
 Exit Code: 0x00
 ###############################################
                                       
 
 
 Exit Code: 0x00
  

Last tutorial I attempted which had a handy script was based off of this thread. 

[https://ubuntuforums.org/showthread.php?t=2190143](https://ubuntuforums.org/showthread.php?t=2190143)

which lead me to here

[https://calomel.org/megacli_lsi_commands.html](https://calomel.org/megacli_lsi_commands.html)

The library this is using is libstorelibir-2.so.14.07-0

I have tried several versions of the software and libs and none seem to work. Which I am guessing from the error its just not detecting it? 

Any help or other software to try would be great. I have not been this stuck in many years. The age of the card I am sure does not help, but it seems to perform quite well.

Thanks in advance for any help.

---

