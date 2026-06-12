---
title: "[SOLVED] Java 1.6.0.0.7 / Ubuntu 8.04"
date: 2008-10-04
forum: General Help
---

### Post by TheSwede86 on 2008-10-04
Hi!

Got a problem when trying to install the latest version of Java (1.6.0.0.7) on Ubuntu 8.04.

My browser is Mozilla v3.3.

First of all I downloaded "jre-6u7-linux-i586.bin" from their offical website.

Copied the file to this folder:
sudo cp /usr/java

Ran it with this:
sudo chmod +x /usr/java/jre-6u7-linux-i586.bin

Then installed it with his:
sudo /usr/java/./jre-6u7-linux-i586.bin

Then when standing in cd /usr/lib/firefox/plugins/
sudo ln -s /usr/java/jre1.6.0_07/plugin/i386/ns7/libjavaplugin_oji.so

But when I close and restart the browser and go back to Java's website it still wants to download plugins and if I click cancel then it says that I don't have Java installed correctly.

Please what is wrong?

I want to get the latest version, not using the 1.6.0.0.6 version which I can get via sudo apt-get install sun-java6-jre

Best Regards & Thanks in advance - TheSwede86

Edit:

Used sudo apt-get install sun-java6-jre instead

---

