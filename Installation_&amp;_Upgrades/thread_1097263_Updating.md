---
title: "Updating"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Botbob89 on 2009-03-15
Hi, when I run

```
sudo apt-get update
```

I get the following come up

```
Err http://archive.canonical.com intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://archive.canonical.com intrepid/partner Translation-en_GB            
  Unable to connect to archive.canonical.com http:
Err http://security.ubuntu.com intrepid-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com intrepid-security/main Translation-en_GB        
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
  Unable to connect to security.ubuntu.com http:
Err http://wine.budgetdedicated.com intrepid Release.gpg                       
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Err http://wine.budgetdedicated.com intrepid/main Translation-en_GB            
  Unable to connect to wine.budgetdedicated.com http:
```

And I have exhausted everything I can think of to solve it...so if you guys have any ideas...?

Thanks in advance

---

### Post by taurus on 2009-03-15
Edit your /etc/apt/sources.list and remove the / after ubuntu and before intrepid for the security repos.

```

deb http://security.ubuntu.com/ubuntu**[COLOR="Red"]/[/COLOR]** intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu**[COLOR="Red"]/[/COLOR]** intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu**[COLOR="Red"]/[/COLOR]** intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu**[COLOR="Red"]/[/COLOR]** intrepid-security universe
deb http://security.ubuntu.com/ubuntu**[COLOR="Red"]/[/COLOR]** intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu**[COLOR="Red"]/[/COLOR]** intrepid-security multiverse

```
Then put a # in front of the last line to comment out the wine repo.

```
**[COLOR="Blue"]#[/COLOR]**deb http://wine.budgetdedicated.com/apt intrepid main
```
Save it and run

```
sudo apt-get update  && sudo apt-get upgrade
```

---

### Post by Botbob89 on 2009-03-15
OK thanks, I've changed /etc/apt/source.lists as you advised and ran

```
sudo apt-get update && sudo apt-get upgrade
```

And now this comes up

```
Err http://archive.canonical.com intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://archive.canonical.com intrepid/partner Translation-en_GB            
  Unable to connect to archive.canonical.com http:
Err http://security.ubuntu.com intrepid-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com intrepid-security/main Translation-en_GB        
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
  Unable to connect to security.ubuntu.com http:
```

---

### Post by taurus on 2009-03-15
What is the whole message error when you run **sudo apt-get update**?

---

### Post by Botbob89 on 2009-03-15
Well it begins by saying

```
0% [Connecting to archive.ubuntu.com (91.189.88.31)] [Connecting to archive.can
```

And stays on that for a few minutes not really doing anything, and then this comes up:

```
Err http://archive.canonical.com intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://archive.canonical.com intrepid/partner Translation-en_GB            
  Unable to connect to archive.canonical.com http:
Err http://security.ubuntu.com intrepid-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com intrepid-security/main Translation-en_GB        
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
  Unable to connect to security.ubuntu.com http:
```

And that is all that comes up, there doesn't seem to be any sort of error message, I have posted everything that appears in the terminal....

---

### Post by taurus on 2009-03-15
Is your network working?  Do you use proxy?

---

### Post by Botbob89 on 2009-03-15
Every aspect of my network is up and running 100% fine apart from this

And yes I use proxy...

---

### Post by dje on 2009-03-15
have you set your proxy settings in System >> Preferences >> Network Proxy?
or run the following command and see if updating works:
```
export http_proxy=*proxy_address*:*proxy_port*
```

dje

---

### Post by taurus on 2009-03-15
Then you need to go into System -> Administration -> Synaptic Package Manager -> Settings -> Preferences -> Network and configure your proxy.  Until then, you cannot update your machine.

---

### Post by Botbob89 on 2009-03-15
Ahhhhh OK, that makes a lot of sense!!

Thanks for the help :)

[SOLVED] Now working absolutely fine, thanks again :)

---

