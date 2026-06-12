---
title: "Can't Install JEE"
date: 2008-11-28
forum: General Help
---

### Post by subuta on 2008-11-28
Hello,

I see that this problem was posted several months ago but, as far as I can tell, no solution was posted.

I am trying to install JEE by running JEE java_ee_sdk-5_06-linux-nojdk.bin  which is of type:

 java_ee_sdk-5_06-linux-nojdk.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped


on ubuntu 8.10

I downloaded it, unzipped it, and chmod'd it:

-rwxr-xr-x  1 dan dan 110462872 2008-11-28 17:38 java_ee_sdk-5_06-linux-nojdk.bin

When I try to run it from bash I get:

dan@scapps1:~/Desktop$ ./java_ee_sdk-5_06-linux-nojdk.bin
bash: ./java_ee_sdk-5_06-linux-nojdk.bin: No such file or directory
dan@scapps1:~/Desktop$ 

If I use sh I get:

dan@scapps1:~/Desktop$ sh java_ee_sdk-5_06-linux-nojdk.bin
java_ee_sdk-5_06-linux-nojdk.bin: 1: Syntax error: "(" unexpected
dan@scapps1:~/Desktop$ 

I have also tried both of the above as sudo and gotten the same results.

Can anyone tell me how to get this bin to run?

Many thanks.

-subuta

---

