---
title: "Ubuntu alternative to Microsoft Internet Information Services"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by androssofer on 2009-05-13
Hello, 

Vista Business allows users to install Microsoft Internet Information Services which basicly allows users to use their computer as a functioning Web server. 

I am currently learning to use Ajax and would like to test my code as I create it, however Ajax requires that the computer operate as a web server to execute certain commands and as such I am unable to run the code. The Microsoft Internet Information Services sets up a directory in Vista that runs like a server that allows Ajax to run. I'm not looking for full server functionality just a simple solution like the MS thing that creates a directory I can save Ajax files to and run the code as if they are on the Internet, in Ubuntu.

Does anyone know of anything i could try? or if Ubuntu already has such a directory?

---

### Post by Artemis3 on 2009-05-13
Well, i think you could just install the package "apache" and the folder would be /var/www :) You could make a symbolic link there to a folder in your home. Do something like this in the terminal:

Make a folder in your user home:
mkdir ~/afolderyoucreate

Then make the symbolic link:
sudo ln -s /home/yourusername/afolderyoucreate /var/www/anynameyoulike

Now put your stuff in /home/yourusername/afolderyoucreate
And browse [http://localhost/anynameyoulike](http://localhost/anynameyoulike)

It is very simple and apache happens to be the most used web server :)
Microsoft IIS is infamous for its numerous vulnerabilities and flaws.

---

### Post by androssofer on 2009-05-13
Cool, sounds gd, thanks.

didnt know i could run Apache on Ubuntu. thanks!

---

