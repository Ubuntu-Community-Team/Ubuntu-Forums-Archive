---
title: "problem installing jdk"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by satyabhat on 2009-08-13
Hi All,

I am trying to install jdk in ubuntu 9.2 Desktop version.
when i give this command sudo apt-get update,i get the following error:


 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

E: Some index files failed to download, they have been ignored, or old ones used instead.
tcs@tcs-desktop:~$ 
tcs@tcs-desktop:~$ touch /etc/apt/apt.conf
touch: cannot touch `/etc/apt/apt.conf': Permission denied
tcs@tcs-desktop:~$ gksudo gedit /etc/apt/apt.conf
tcs@tcs-desktop:~$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_IN                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_IN              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_IN                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_IN              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_IN            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_IN      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_IN          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_IN    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_IN      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_IN    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_IN                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_IN                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_IN              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_IN              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages                       
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                          
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_IN
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_IN   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN    
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                 
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages           
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/multiverse Translation-en_IN
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages             
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

i have added http_proxy=http://username:password@host:port/
export http_proxy in /.bashrc

is there anythying else tht i need to do.
Please help !!!:confused:

---

### Post by Partyboi2 on 2009-08-13
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to these two commands
```
lsb_release -d
```
and
```
cat /etc/apt/sources.list
```

---

### Post by Pushpalanka on 2010-12-13
[FONT=Century Gothic][SIZE=3]root@pushpalanka-laptop:/home/pushpalanka/Desktop# apt-get install sun-java6-jdkE: Malformed line 46 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.[/SIZE][/FONT]

I got the above error when i tried to install jdk6. Grateful if anyone can give me a quick help.

Also I have downloaded "**jdk-6u23-linux-i586.bin**" and all the methods i tried ended up unsuccessful. What is the easiest and reliable method to install it. what commands can i use?????????

---

### Post by lykeion on 2010-12-13
If those are the next generation of Java developers I guess Java is in deeper trouble than it already is (=joke).

Both OP and the other guy hijacking the thread need to fix their sources.lst before they can install anything.

I'd suggest you do what Partyboi2 says so we can help you fix it, but ***do enclose command output in CODE tags*** using the # button. Otherwise it's pretty unreadable.

---

