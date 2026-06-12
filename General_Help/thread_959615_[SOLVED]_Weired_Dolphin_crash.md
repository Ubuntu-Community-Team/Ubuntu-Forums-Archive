---
title: "[SOLVED] Weired Dolphin crash"
date: 2008-10-26
forum: General Help
---

### Post by Jense on 2008-10-26
Hi everybody,

the latest update somehow messed up the permissions (I think) for dolphin. 
Here is the problem:
I start dolphin as normal user an get the following response in terminal> jens@jens-mobile:~$ dolphin
<unknown program name>(15710)/: Communication problem with  "dolphin" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive areply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "

jens@jens-mobile:~$

Obviously dolphin doesn't start... so I do the same thing as superuser and dolphin does start, though apperently going through a rough time to do so:
> jens@jens-mobile:~$ sudo dolphin
[sudo] password for jens:       
Error: "/var/tmp/kdecache-jens" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jens" is owned by uid 1000 instead of uid 0.         
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"                                                    
Loading simple Config module ...                                                
Creating backend ...                                                            
Loading socket FrontEnd module ...                                              
Starting SCIM as daemon ...                                                     
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"                                                    
dolphin(15417) MetaDataWidget::setFile: KUrl("file:///home/jens")               
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"                                                    
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"                                                    
<unknown program name>(15412)/: Communication problem with  "dolphin" , it probably crashed.                                                                    
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "                                             

jens@jens-mobile:~$ Error: "/tmp/ksocket-jens" is owned by uid 1000 instead of uid 0.                                                                           
dolphin(15417) MetaDataWidget::setFile: KUrl("file:///home/jens")               
dolphin(15417) MetaDataWidget::setFile: KUrl("file:///home/jens")               
dolphin(15417) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"                                                                               
dolphin(15417) KMimeTypeFactory::parseMagic: Now parsing  "/home/jens/.local/share/mime/magic"
dolphin(15417) MetaDataWidget::setFile: KUrl("file:///home/jens/Desktop")
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(15417)" Error in thread 3051640512 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
kDebugStream called after destruction (from void KDirWatchPrivate::removeEntry(KDirWatch*, const QString&, KDirWatchPrivate::Entry*) file /build/buildd/kde4libs-4.1.2/kio/kio/kdirwatch.cpp line 771)
path= "/home/jens/.local/share//user-places.xbel" sub_entry: 0x0
kDebugStream called after destruction (from void KDirWatchPrivate::removeEntry(KDirWatch*, KDirWatchPrivate::Entry*, KDirWatchPrivate::Entry*) file /build/buildd/kde4libs-4.1.2/kio/kio/kdirwatch.cpp line 821)
Cancelled INotify (fd 9, 1) for "/home/jens/.local/share//user-places.xbel"
kDebugStream called after destruction (from void KDirWatchPrivate::removeEntry(KDirWatch*, KDirWatchPrivate::Entry*, KDirWatchPrivate::Entry*) file /build/buildd/kde4libs-4.1.2/kio/kio/kdirwatch.cpp line 846)
Removed File "/home/jens/.local/share//user-places.xbel" for "" ["KDirWatch-1"]


I really don't know what to make of that so if anybody can help.. thanks a lot.

System is Intrepid still and KDE 4.1

---

### Post by SuperSonic4 on 2008-10-26
I would imagine it is because root owns dolphin. What happens if you chown it to user?

---

### Post by Jense on 2008-10-26
I tried to chown it, but I think I am not doing this right...

> jens@jens-mobile:~$ sudo chown jens:jens dolphin
chown: Zugriff auf &#8222;dolphin&#8220; nicht möglich: No such file or directory


Ok now I found dolphin in /usr/bin/.. and could chown it, but the problem is still there and I think also that the user not having ownership of the file "dolphin" is not related to the problem at hand, because dolphin does start it just sits there and waits for some other service. That service is owned by root and thats why I can start dolphin as root. However I would think that there is a reason for the root ownership... so any ideas?

---

### Post by Jense on 2008-10-27
Ok, found the solution on launchpad... I had to delete
> /home/[username]/.kde/share/config/dolphinrc file
and login once more, now dolphin is back, for whatever reason. Hope this helps if somebody else has the same problem.

---

