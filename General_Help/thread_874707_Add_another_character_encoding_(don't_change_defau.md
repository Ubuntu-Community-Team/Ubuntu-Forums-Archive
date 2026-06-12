---
title: "Add another character encoding (don't change default encoding)"
date: 2008-07-30
forum: General Help
---

### Post by HamburgerTS on 2008-07-30
My system (ubuntu 8.04) only knows UTF-8 encoding and i'm forced to edit some files from a windows system which are encoded as "us-ascii" (i think this implies cp1252 because cp1252 is the default encoding on the windows system). 

Due to that i "want" to make the needed encoding available on my system. 

An older source (from the year 2006 for Dapper Drake) described this solution: 

1. installation of localeconf
```
sudo apt-get install localeconf
```

2. Edit file /var/lib/locales/supported.d/de as Root 
```
sudo vi /var/lib/locales/supported.d/de. 
```
   Append the following line:
```
de_DE@euro ISO-8859-15
```

3. Save the file and generate /etc/locale.gen
```
sudo dpkg-reconfigure locales
```

4. Via localeconf system wide selection of the new character encoding: ```
sudo dpkg-reconfigure localeconf 
```


Source (German): [http://www.linux-community.de/Neues/story?storyid=20090](http://www.linux-community.de/Neues/story?storyid=20090)
---
Can someone please tell me if this solution is still accurate or not? (And if not give me some hints for further searching?)

Many thanks in advantage..
Martin

---

### Post by HamburgerTS on 2008-07-31
Hello again,

i just realised that the wanted character encoding is available in

```
Choose Terminal &#9656; Set Character Encoding &#9656; Add or Remove > Available encodings list box
```
            
Because of that i assume that the wanted encoding is already installed on my system (named "Wester WINDOWS-1252"). 

Can somebody please confirm that? A enconding appearing in the above mentioned dialog is available system wide?

---

