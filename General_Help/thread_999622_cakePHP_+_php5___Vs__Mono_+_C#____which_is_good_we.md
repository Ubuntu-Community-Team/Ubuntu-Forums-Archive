---
title: "cakePHP + php5   Vs  Mono + C#    which is good web development platform for linux?"
date: 2008-12-02
forum: General Help
---

### Post by jittopjose on 2008-12-02
hello friends,
currently i am a asp.net/C# developer. if we wish to build an enterprise class web application with development and server platform as ubuntu, which technology is more reliable and ease of use?...  cakePHP or mono/C# ?

could u please give me some suggestions.  we a group of people are thinking of starting a new company. we have got some enterprise class project suggestions. we must have to stick with linux platform as we dont have much capital.. 

kindly forgive me if am pushing any redundant discussion thread. 
thank you
jittos....

---

### Post by kernelhaxor on 2008-12-02
I do not know much about Mono but I have developed many ASP.net/C# applications on Windows platform and have also developed PHP5 web app using CakePHP framework.

If you build a ASP .net web application, I am not sure but don't you need a ASP.net/Windows server? (And I think that license is quite expensive?)  How can you use Ubuntu as the server platform?

On the other hand, PHP works very good with Ubuntu .. and it would be a much economical solution.  From my experience with CakePHP, I can say that it scales well and is a very good rapid development framework but it does take some time to get used to and figure out the various things.  Since you also say, you are a asp developer, there will be a learning curve obviously but PHP is not at all a difficult language.

So if you don't want to pay for server licenses, CakePHP+PHP5 would be a very gud choice.

---

### Post by dgoosens on 2008-12-02
I would go for LAMP
(= Linux, Apache, MySQL, PHP) and if you really want professional stuff have a look at the ZEND MVC framework (or Symfony...).

---

### Post by jittopjose on 2008-12-02
i was telling about mono/C#  which can be deployed on an apache server. so we can host it in a linux server. i studied cakePHP using some tutorials.. i dont have much knowledge in php but i felt its not that difficult to study. 
but my question is , whether this cakePHP is capable of building big enterprise class softwares like doument management, project management for engineering filed etc? i have seen such softwares only in .net and java... thats why i asked.

---

### Post by kernelhaxor on 2008-12-02
> **jittopjose said:**
> 
but my question is , whether this cakePHP is capable of building big enterprise class softwares like doument management, project management for engineering filed etc? i have seen such softwares only in .net and java... thats why i asked.

Not sure about how easy/hard it would be to do things that you are talking about but when you say 'big', if you mean the number of users, I can say that cakephp does scale.  The company I worked for which used CakePHP + PHP5 (Lamp stack) has over 1.5 million users.
For things like document processing, doc management and stuff, I don't know.

---

### Post by dgoosens on 2008-12-02
PHP really is a web language and is not really meant to build software...
but there is the PHP4Mono project that should enable you to write software with PHP
[http://php4mono.sourceforge.net/]("http://php4mono.sourceforge.net/")
I have not had time to have a close look at it though... 

but if you want to build software, that would be cross-platform on top of it, mono and C# would be a good pick

---

### Post by jittopjose on 2008-12-02
one more thing... i heard, cakePHP support ORM by default. but not mono or asp.net.  that is, i need to write stored procedures to avoid inline query. there is one option 'Nhibernate', but dont know how much reliable it as we didnt use it ever in out asp.net project.
i am in confusion.... many people says that php is something a web development language... but not meant for big projects which handles sofisticated algorithms and all.... some says that its less secure that .net...  am really confused.....

---

### Post by directhex on 2008-12-02
> **kernelhaxor said:**
> If you build a ASP .net web application, I am not sure but don't you need a ASP.net/Windows server? (And I think that license is quite expensive?)  How can you use Ubuntu as the server platform?

mono-apache-server2 package, then libapache2-mod-mono package.

---

### Post by jittopjose on 2008-12-02
anybody know any good easy to use ORM solution for mono / C# ?..

---

### Post by directhex on 2008-12-02
Warning: subjective opinion

IME, PHP "makes sense" as a way to build "smart" web *pages*. Taking HTML, making that HTML "smarter" is easy with PHP. Conceptually, it makes sense. Conversely, Whilst PHP makes sense for *pages*, I've found it more than a little lacking for coherent *sites*. When people talk about poor scalability they don't mean that PHP can't have lots of users (it can), but it's an absolute pig to maintain and keep secure past a certain site size.

ASP.NET on the other hand is designed for "sites" - but is extremelt difficult conceptually if you come from an HTML background (great from an app background though). I've tried to write some ASP.NET before, and simply failed at it.

JSP lies in the middle, allowing a little of both - you can easily write JSP the way you'd write PHP, but you can also do all the "Enterprise" back-end stuff that ASP.NET does well and PHP does poorly.

---

### Post by directhex on 2008-12-02
> **jittopjose said:**
> anybody know any good easy to use ORM solution for mono / C# ?..

    *  db4o ([http://www.mono-project.com/DB4O](http://www.mono-project.com/DB4O)) is an open source object database for .NET and Mono, a non-intrusive persistence system that stores any complex object with one single line of code.
    * NHibernate ([http://wiki.nhibernate.org/display/NH/Home](http://wiki.nhibernate.org/display/NH/Home)) NHibernate is a .NET based object persistence library for relational databases. NHibernate is a port of the excellent Java Hibernate relational persistence tool. 

from [http://www.mono-project.com/Database_Access](http://www.mono-project.com/Database_Access)

---

### Post by jittopjose on 2008-12-02
is it possible to create desktop client using php. i saw one project called PHPGTK..? is it good for gui programming?.. any designer for gui applictions?... like glade for gtk. any idea about it?

---

### Post by jittopjose on 2008-12-02
is it possible use glade designer itself for php-gtk development?

---

### Post by directhex on 2008-12-03
> **jittopjose said:**
> is it possible to create desktop client using php. i saw one project called PHPGTK..? is it good for gui programming?.. any designer for gui applictions?... like glade for gtk. any idea about it?

Terrible at it, and all the demons of Hades will feast upon your soul for trying it

---

### Post by udayrajb on 2010-02-03
Instead of trying to learn PHP, you should turn to J2EE. You already know C#, so migrating to Java will be easy. All OSes have excellent support for Java, J2EE Web Applications.

---

