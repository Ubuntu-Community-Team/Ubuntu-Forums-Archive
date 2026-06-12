---
title: "Use the HOSTS file"
date: 2008-11-03
forum: General Help
---

### Post by Luis Cisneros Jr on 2008-11-03
Reposted from [IYCC.org]("http://www.iycc.org/node/329/"):

Are you tired of ads on your web browser? Tired of websites redirecting you to not-so-family-friendly websites (unless you don't mind that)? Want to put a stop to this? Learn to use the HOSTS file to your advantage. Network administrators use the HOSTS file for testing, configuring, or block website access. The HOSTS file can be a powerful tool in your computer arsenal if you know how to use it. Plus, the HOSTS file is free and does not need to be downloaded. Your Linux, Windows, Mac machines and others have the HOSTS file already installed ready to be use. 

Without getting too technical, you can think of your computer's HOSTS file as a personal phone book. When you type a domain name in your web browser, the global DNS points your computer to the IP address matching the domain name in its phone book. Before your computer looks at the DNS's phone book, your computer looks at its phone book first and since your computer looks at its phone book first before DNS's, you can take control of your computer from pointing to the IP address of ads, adult sites, malicious websites, and the such. 

Let us assume you have opened your computer's HOSTS file (I'll show you how for Linux and Windows later) with a text editor. You should see two columns of information somewhere in the HOSTS file. The first column should be the IP address '127.0.0.1' and in the second column next to the IP address is the word 'localhost.' The &#8220;127.0.0.1' IP address is your computer's IP address. If you type the IP address and/or the localhost in your web browser, you should receive a variance of 'Page Not Found.' That is because your computer is searching for a page that isn't there. Let's try something to demonstrate to you the potential of modifying the HOSTS file. 

Create a new row underneath the localhost row by hitting the Enter key. Your cursor should now be below the localhost row. Type the IP address '127.0.0.1' first then hit the tab key and type 'www.google.com.' Save the changes in your text editor. Go to Google's website. If you see Google, refresh the page. If you still see Google, close the web browser you have opened and open the web browser again. If you don't have Google as your home page, type 'www.google.com' in the address bar and see what happens. Look, Google is off line! Try refreshing the page. Nothing just a dead page. Your computer looked at the HOSTS file first and saw 'www.google.com' goes to the '127.0.0.1' IP address so your computer doesn't go out to see the Google listing in the global phone book, the DNS. You can get Google back by deleting the 'www.google.com' entry in your HOSTS file or by commenting the entry out by placing the # symbol before the IP address. 

Let us try another demonstration. Go to [www.pcmag.com](www.pcmag.com). There are lots of pictures on the front page. In the HOSTS file, type the '127.0.0.1' IP address, hit the tab key, then type 'common.ziffdavisinternet.com.' Save the change in your text editor and refresh the PCMag.com page. Now, the pictures are gone from the front page. The images are actually located on the common.ziffdavisinternet.com site and not on [www.pcmag.com](www.pcmag.com). You can use the HOSTS file to block ads and websites altogether. But there is a catch. The HOSTS file isn't very 'smart.' It doesn't see [www.google.com](www.google.com) as the same as google.com (without the www). So, if you want to block ads and websites, you need to place the domain name of those ads and malicious websites with and without the 'www.' prefix. And you might need to add other prefixes of the same domain name. ([www.google.com](www.google.com), google.com, images.google.com, mail.google.com). The HOSTS file is very effective you are willing to make the modifications. 

To modify the HOSTS file in Windows, search for HOSTS in Windows under the 'C:\Windows\system32\etc' directory. The HOSTS file for Windows NT is under the &#8220;C:\Windows\Winnt&#8221; if I'm not mistaken. For Linux users, open a terminal, become the root user, then type: 

[CENTER]'nano /etc/hosts' [/CENTER]

Make the time to experiment with the HOSTS file. Over time, your computer will be free from ads, adult sites, malicious sites, and other places to cause trouble.

---

