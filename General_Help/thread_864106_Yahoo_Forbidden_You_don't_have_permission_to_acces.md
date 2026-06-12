---
title: "Yahoo Forbidden You don't have permission to access"
date: 2008-07-19
forum: General Help
---

### Post by aboutwebdesign on 2008-07-19
I am a website designer and a couple of people are apparently having issues accessing a site that I built.
[http://www.irishveteransmemorialproject.com](http://www.irishveteransmemorialproject.com)

They are getting this message when trying to access:

Yahoo Forbidden You don't have permission to access
/SIG=120pth7ed/EXP=1216052580/**http%253A/www.irishveteransmemorialproject.com/ on this server.

I have no problem accessing the site myself so I'm not sure what's going on......I am not using a database on the site either, it's pure html and javascript.....What are my options?

About Web Design
[http://www.aboutwebdesign.ie](http://www.aboutwebdesign.ie)

---

### Post by cpetercarter on 2008-07-19
This looks like the sort of message thrown up by software such as Bad Behaviour, which attempts to block access to the site by "suspicious" computers, but catches a lot of innocent parties in the process. Is it perhaps being run by your web-hosting service?

---

### Post by songshu on 2008-07-19
no problem here if its any good to you.

The Irish Veterans Historical Research Centre is Ireland's only registered charity dedicated to establishing and maintaining a memorial dedicated to all Irish men and women who served, and in particular those who made the ultimate sacrifice, in foreign military forces from 1900 to the present day.

---

### Post by aboutwebdesign on 2008-07-19
So it's not a coding issue? what are my options, should I contact my web server or is there any point? 

About Web Design
[http://www.aboutwebdesign.ie](http://www.aboutwebdesign.ie)

---

### Post by cpetercarter on 2008-07-19
A google search suggests that this may be an error thrown up by the Yahoo search engine - were the visitors to your site using Yahoo?

---

### Post by aboutwebdesign on 2008-07-19
They didn't say, but I can ask them. If they were using Yahoo, do they just have to use another search engine?

About Web Design
[http://www.aboutwebdesign.ie](http://www.aboutwebdesign.ie)

---

### Post by songshu on 2008-07-19
is your site perhaps blocking search engine spiders?

it could be that its thinking that the redirections from yahoo is an indexing attempt.

but thats a guess...

---

### Post by gunashekar on 2008-07-19
If your site is hosted on a shared server, check the backend (example CPanel) options one by one. 
See if your website root has a file such as robots.txt that blocks web spiders.

---

### Post by aboutwebdesign on 2008-07-21
Checked to see if there was a spiders.txt in my Cpanel but didn't find it. Starting to think that it may be the fact that there is flash animation in the site and the users that are having the problems don't have the latest version of flash player. Have you guys ever heard of this happening?

---

### Post by songshu on 2008-07-21
if the visitors are being blocked or even reach your site with an error, it would probably show up in your http or firewall logs i would assume.

if not, do you have a hosting company that might block it?

---

