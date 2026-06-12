---
title: "problems with Java webpages"
date: 2008-09-15
forum: General Help
---

### Post by Raval on 2008-09-15
I have trouble with my Bank's website after filling out my login info I click on the log in button but nothing happens. 

I am only able to gain access IE7 through VirtualBox.

URL: [https://republiconline.republictt.com/corp/BANKAWAY?Action.RetUser.Init.001=Y&AppSignonBankId=090&AppType=corporate](https://republiconline.republictt.com/corp/BANKAWAY?Action.RetUser.Init.001=Y&AppSignonBankId=090&AppType=corporate)

I have OpenJDK installed (build 1.6.0_06-b02)

---

### Post by fooman on 2008-09-15
have you tried installing jre?  in synaptic or in a terminal:

```
sudo apt-get sun-java6-jre
```

---

### Post by Raval on 2008-09-15
> **fooman said:**
> have you tried installing jre?  in synaptic or in a terminal:

```
sudo apt-get sun-java6-jre
```

yes Sun-Java6-jre, Sun-Java6-plugin and Sun-Java6-bin are installed

---

### Post by luvr on 2008-09-15
I can only confirm what **fooman** said: you should definitely install Sun's Java Run-Time Environment. It's how I solved my problem with AXA Belgium online banking.

You may wish to remove OpenJDK first (it's optional, but it's what I did), e.g., with Synaptic: Select all *"openjdk"* packages for complete removal, and apply the changes.

To install the Sun JRE, here's the command that I used:
```
sudo apt-get install sun-java6-plugin sun-java6-fonts
```
I believe that fooman's command will do the job as well, but I wanted to make absolutely, positively sure that the Plugin (for running Java within the browser) was installed--which is why I requested it explicitly; the dependencies among the packages will ensure that the actual JRE will be pulled in as well.

Then, to verify if the Sun JRE is actually the default Java environment (this is particularly important if you left OpenJDK installed), you may want to run the following command:
```
sudo update-alternatives --config java
```
If you have more than one Java environment installed, this command will ask you to select the one that should become the default; be sure to select the Sun JRE.

Incidentally, I notice that [RepublicOnline]("https://republiconline.republictt.com/website_requirements.htm") also requires the Adobe Reader plug-in. Be sure to install the actual reader from Adobe--the free software alternatives are highly unlikely to work in this context (in my experience). Use the following command to install the Adobe Reader and its plug-in:
```
sudo apt-get install acroread-plugins mozilla-acroread
```
If that's insufficient to make the plug-in work, then you must be missing a link to the plug-in. I remember that I did create the link, but I'm not sure if it was really required; if it is, though, then here are the commands to create it:
```
cd /usr/lib/firefox-addons/plugins
sudo ln -s /usr/lib/Adobe/Reader8/Browser/intellinux/nppdf.so nppdf.so
```

Lastly, [RepublicOnline]("https://republiconline.republictt.com/website_requirements.htm") also seems to want Adobe Flash Player; I believe that Firefox will guide you through the required installation process if you don't have that installed yet when it's needed.

---

### Post by philinux on 2008-09-15
I'd try this addon. If all else fails.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by Raval on 2008-09-15
I got it working.

I removed OpenJDK and also disabled Java console plugin in Firefox.

---

