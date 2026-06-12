---
title: "Good times with Pidgin and Kopete"
date: 2008-11-29
forum: General Help
---

### Post by windoze87 on 2008-11-29
This problem's a little wiggy, and i have no clue how to fix it. Here's my problem- I have both Pidgin and Kopete installed on my Ubuntu 8.04.1 install. I havent had an issue at all with Ubuntu or any programs for so long i was starting to think i was overdue for one, and i was right. I use Pidgin mainly for the most part, but use Kopete for those rare times that Pidgin acts up. But here's the deal- for a while now ( i can't exactly remember when it started up, probably around the time that the 2.6.24-21 kernel got plopped on my system, but i can't be specific, because i honestly dont remember) both Kopete and Pidgin take a godawful amount of time connecting to the Yahoo server. It isn't my account, because for one, they always eventually connect (pidgin usually does it faster) and i also booted into Windows, fired up Yahoo Messenger 9 beta, and it signs me right in. I do notice that it takes longer if i have other protocols trying to connect (like if im trying to connect to the MyspaceIM protocol and Live Messenger), and if i shut them off, it will speed things up, but im still twiddling my fingers for a few minutes. I tried reinstalling and uninstalling both of them, even using --purge, and it did no good. I cannot get pidgin to give me any feedback in terminal, it just sits there like a dead goat till my Yahoo contacts pop up. However, kopete gives me this: ```
rick@source:~$ QMetaObject::findSignal:ClientStream: Conflict with Stream::readyRead()
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: ListTask
QGArray::find: Index 0 out of range
Transfer ACCEPTED by: ListTask
CLIENT: RequestPictureTask: Task::done()
CLIENT: RequestPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: RequestPictureTask: Task::done()
CLIENT: RequestPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
Transfer ACCEPTED by: MailNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
QGArray::find: Index 0 out of range
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
Transfer ACCEPTED by: PictureNotifierTask
Transfer ACCEPTED by: PictureNotifierTask
QMetaObject::findSignal:ClientStream: Conflict with Stream::readyRead()
QObject::disconnect: No such signal Client::gotBuddyIconRequest(const QString&)
QMetaObject::findSignal:ClientStream: Conflict with Stream::readyRead()
KCrash: Application 'kopete' crashing...

```
i had already signed into MSN. As soon as i fired up Yahoo,i get all this, and bam, kopete dies. Kopete WILL connect to Yahoo occasionally though. Pidgin almost always does it without having to quit & fire it back up again. I dont have any firewall rules set (to my knowledge, anyway) to block any of these protocols. So what should i do? thanks for any help you guys can give.

---

