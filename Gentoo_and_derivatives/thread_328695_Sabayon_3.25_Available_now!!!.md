---
title: "Sabayon 3.25 Available now!!!"
date: 2006-12-31
forum: Gentoo and derivatives
---

### Post by RAV TUX on 2006-12-31
As per usually bleeding edge Linux that "Just Works"

---

### Post by RAV TUX on 2007-01-01
Sabayon 3.25 should be out tomorrow...

It will be the first Linux distro to have KVM:
> 
White Paper
 **The K virtual machine (KVM)**

Share This Page[LIST]
[*][ *del.icio.us*]("http://del.icio.us/post?v=4;url=http%3A%2F%2Fjava.sun.com%2Fproducts%2Fcldc%2Fwp%2F;title=The%20K%20virtual%20machine%20%28KVM%29")
[*][ *digg.com*]("http://digg.com/submit?phase=2&url=http%3A%2F%2Fjava.sun.com%2Fproducts%2Fcldc%2Fwp%2F&title=The%20K%20virtual%20machine%20%28KVM%29")
[*][ *slashdot.org*]("http://slashdot.org/bookmark.pl?title=The%20K%20virtual%20machine%20%28KVM%29&url=http%3A%2F%2Fjava.sun.com%2Fproducts%2Fcldc%2Fwp%2F")
[*][ *technorati.com*]("http://www.technorati.com/search/http%3A%2F%2Fjava.sun.com%2Fproducts%2Fcldc%2Fwp%2F")[/LIST]
                      [[IMG]http://java.sun.com/im/ic_print.gif[/IMG]Print-friendly Version]("http://java.sun.com/jsp_utils/PrintPage.jsp")

**A White Paper**

  [SIZE=-1]Also available in [/SIZE][SIZE=-1][PDF]("http://java.sun.com/products/kvm/wp/KVMwp.pdf").[/SIZE] 
 The purpose of this paper is to describe the choices made by Sun's KVM technology team when designing the K virtual machine (KVM) for consumer and embedded devices.
  
[IMG]http://java.sun.com/im/a.gif[/IMG]
  **Table of Contents**

 [Executive Summary]("http://java.sun.com/products/cldc/wp/#executive")
[Introduction to the Java 2TM Micro Edition]("http://java.sun.com/products/cldc/wp/#intro")
- [Configurations]("http://java.sun.com/products/cldc/wp/#configurations")
- [Profiles]("http://java.sun.com/products/cldc/wp/#profiles")
[Features of the K Virtual Machine and its APIs]("http://java.sun.com/products/cldc/wp/#features")
- [The KVM Specification]("http://java.sun.com/products/cldc/wp/#spec")
- [The KVM Optional Features]("http://java.sun.com/products/cldc/wp/#optional")
  - [The Java2 Micro Edition Core APIs]("http://java.sun.com/products/cldc/wp/#micro")
    - [Basic Classes from java.lang]("http://java.sun.com/products/cldc/wp/#basic")
    - [Throwable Classes from java.lang]("http://java.sun.com/products/cldc/wp/#throwable")
    - [Data Type Classes from java.lang]("http://java.sun.com/products/cldc/wp/#data")
    - [String Classes from java.lang]("http://java.sun.com/products/cldc/wp/#string")
    - [Miscellaneous Classes from java.lang]("http://java.sun.com/products/cldc/wp/#misc")
    - [Miscellaneous Classes from java.util]("http://java.sun.com/products/cldc/wp/#classes")
[Optimizations for Consumer Devices]("http://java.sun.com/products/cldc/wp/#optimizations")
- [Engineering a small footprint core API]("http://java.sun.com/products/cldc/wp/#engineering")
[Design Considerations for the KVM]("http://java.sun.com/products/cldc/wp/#design")
- [Portability]("http://java.sun.com/products/cldc/wp/#portability")
- [Garbage Collection]("http://java.sun.com/products/cldc/wp/#garbage")
- [Host System Calls]("http://java.sun.com/products/cldc/wp/#host")
[Conclusion]("http://java.sun.com/products/cldc/wp/#conclusion")  
[IMG]http://java.sun.com/im/a.gif[/IMG]
  **Executive Summary**

 Over the last two years Sun has introduced tailored JavaTM virtual machine technology to serve products in the consumer and embedded markets. With [PersonalJava]("http://java.sun.com/products/personaljava/index.jsp")TM technology targeted at screen phones, high end PDAs and set top boxes, and [Java Card]("http://java.sun.com/products/javacard/index.jsp")TM technology targeted at smart cards, Sun has greatly extended the scope of the Java programming environment. In the process, Sun has demonstrated the versatility of this environment and enabled the development of many new and powerful information appliance products. The [K virtual machine (KVM)]("http://java.sun.com/products/cldc/index.jsp") is Sun's newest Java virtual machine technology and is designed for products with approximately 128K of available memory. The KVM fills a very important role in Sun's Java virtual machine product offerings, and will form a part of a completely new Java runtime environment. This environment is highly optimized for small-memory limited-resource connected devices such as cellular phones, pagers, PDAs, set-top boxes, and point-of-sale terminals.
 The KVM has been developed as part of larger effort to provide a modular, scalable architecture for the development and deployment of portable, dynamically downloadable, and secure applications in consumer and embedded devices. This larger effort is called the [Java 2 Platform Micro Edition]("http://java.sun.com/j2me/index.jsp") (Java 2 ME). Connected, personalized, intelligent tools are becoming increasingly important in our business and private lives. Java 2 ME is an architecture designed to address the specific technical requirements of these new information appliances.
 While connected consumer devices like pagers, cell phones and PDAs have many things in common, they are also diverse in features, form, and function. Information appliances tend to be special-purpose, limited-function devices, not general-purpose computing machines like servers and desktop systems. Serving this market calls for a large measure of flexibility in how Java technology is deployed. Flexibility in deployment is also important because over the lifetime of any one connected device, its applications and capabilities can change and grow to accommodate the needs of the user. Users want the ability to purchase economically priced products with basic functionality and then use them with ever-increasing sophistication. Java technology enables users, service providers, and device manufacturers to take advantage of a rich portfolio of application content that can be delivered to the user's device on demand, by wire or over airwaves.
 The Java 2 ME architecture is modular and scalable so that it can support the kind of flexible deployment demanded by the consumer and embedded markets. For low-end, resource-limited products, Java 2 ME and the KVM support minimal configurations of the Java virtual machine and Java APIs that capture just the essential capabilities of each type of device. As device manufacturers develop new features in their devices or service providers develop new and exciting applications, these minimal configurations can be expanded with additional APIs or with a richer complement of Java virtual machine (Java VM) features. While the KVM is targeted at devices containing 16- or 32-bit processors and a total memory footprint of approximately 256K bytes, KVM can be deployed flexibly to address a range of trade-offs between space and functionality. In addition, Java 2 ME provides a range of virtual machine technologies, each optimized for the different processor types and memory footprints commonly found in the consumer and embedded marketplace.
 The KVM is engineered and specified to support the standardized, incremental deployment of the Java virtual machine features and the Java APIs included in the Java 2 ME architecture. The Java 2 ME architecture defines a small core API which must be fully implemented in every Java 2 ME compatible device. Java 2 ME is deployed in several configurations. Each configuration addresses a particular "class" of device and specifies a set of APIs and Java virtual machine features that users and content providers can assume are present on those devices when shipped from the factory. Application developers and content providers must design their code to stay within the bounds of the Java virtual machine features and APIs specified by that configuration. In this way, interoperability can be guaranteed among the various applications and devices in a particular class.
 The purpose of this paper is to describe the choices made by Sun's KVM technology team when designing the K virtual machine for consumer and embedded devices.
 [Chapter 2]("http://java.sun.com/products/cldc/wp/#intro") of this white paper sets the stage for this discussion by providing an introduction to the Java 2 Micro Edition. Then [Chapter 3]("http://java.sun.com/products/cldc/wp/#features") reviews the proposed features of the KVM and API, and discusses how the features of the VM are related to the definition of Java 2 ME configurations. [Chapter 4]("http://java.sun.com/products/cldc/wp/#optimizations") reviews the optimizations that went into designing the KVM as well as the Java 2 ME core API. [Chapter 5]("http://java.sun.com/products/cldc/wp/#design") summarizes the considerations that went into the design of the KVM and API. Finally, [Chapter 6]("http://java.sun.com/products/cldc/wp/#conclusion") discusses the future direction of the KVM technology.
 
**Introduction to the Java 2 Micro Edition**

 The [Java 2 Micro Edition]("http://java.sun.com/j2me/index.jsp") encompasses the full range of products, technology, tools and standards needed to enable the information appliance market. It currently includes two different implementations of the Java virtual machine:[LIST]
[*]**A Java virtual machine suitable for 32-bit RISC/CISC/DSP microprocessors** and a few megabytes of working memory. Typical products in this market include screen phones, set-top boxes and high-end PDAs.
[*]**A Java virtual machine suitable for 16-bit or 32-bit RISC/CISC microprocessors** with a few hundred kilobytes of available memory. Typical products in this market include cell phones, low- to mid-range PDAs and low-end set-top boxes.[/LIST]Because Java 2 ME includes both in-device and off-device elements, it provides an end-to-end architecture for device manufacturers, service providers, and independent software vendors. The end-to-end architecture leverages and integrates such key Sun technologies as [Jini]("http://www.sun.com/jini/")TM and [Java Embedded Server]("http://www.sun.com/software/embeddedserver/")TM. 
**Configurations**

 The Java 2 Micro Edition can be deployed in multiple configurations. A configuration is defined as a set of optimized Java APIs, class libraries and a virtual machine targeting a family of devices with similar requirements on size and capabilities. Configurations include components of the java.io, java.net, java.util, and the java.lang packages. Sun, in conjunction with industry partners, will define and evolve the Java 2 Micro Edition and its configurations. This is done with the JCP (Java Community Process). The Java 2 Micro Edition includes two standard configurations, which are subsets of the Java 2 Standard Edition core APIs, and which will fit in 128k of ROM.
 
**Profiles**

 An additional way of specifying the subset of Java APIs, class libraries and virtual machine features that targets a specific family of devices is the profile.  A profile is a collection of Java technology-based class libraries and APIs and a specific configuration that provides domain-specific capabilities for devices in a specific vertical market. 
 
**Features of the K Virtual Machine and its APIs**

 This section describes the K virtual machine (KVM). It also describes the classes and methods included in the Java 2 ME API. Although the latter topic is not strictly a component of the KVM technology, it is essential to understand how the KVM is applied in resource-limited products. 
**The KVM Specification**

 The KVM evolved from a research project at Sun Laboratories. It is a derivative of The Java Virtual Machine Specification, written from scratch in C, with special emphasis in these key areas:[LIST]
[*]Optimized for small size
[*]Easily portable to different platforms
[*]Modular and extensible
[*]Source code base written from scratch
[*]As "complete" and "fast" as possible without significantly increasing footprint.[/LIST]Except for the differences indicated in the following section, the KVM is identical to the Java virtual machine as specified in [The Java Virtual Machine Specification]("http://java.sun.com/docs/books/vmspec/") (Java Series) by Tim Lindholm and Frank Yellin (second edition, Addison-Wesley, 1999). 
**The KVM Optional Features**

 The KVM is designed to support standardized, incremental deployment of Java virtual machine features and Java APIs called for by the Java 2 ME architecture. The KVM specification identifies several optional features which can be omitted from some minimum initial device configurations, depending on the features and capabilities of the device. The Java 2 ME architecture includes a small number of configurations that are specified and standardized by Sun. The KVM specification gives the guidelines that Sun uses in defining configurations. It spells out exactly which features can be omitted from an initial configuration. The following features defined in The Java Virtual Machine Specification are optional in the KVM architecture. In each case, a feature is designated "optional" because:[LIST=1]
[*]The applications designed for a particular configuration (or class of device) do not need the feature.
[*]Elimination of the feature significantly reduces memory footprint or enables some other cost savings or necessary functionality in the class of device targeted by that configuration.[/LIST]While these features are optional at the KVM architectural level, they may be required at the KVM implementation level. Each Java 2 ME configuration specifies whether or not each optional feature is included. Any KVM implementation claiming to support a particular configuration must implement all the features required by that configuration. Features not explicitly identified in the following list are required and must be implemented in all configurations.[LIST]
[*]**Large data types: long, float, and double** -- many configurations do not need the extended range and precision of the larger data types.
[*]**Multi-dimension arrays** -- many configurations do not need to support arrays of more that one dimension.
[*]**Class file verification** -- some specified configurations may not need to support on-device verification of class files. Instead technology is planned to be developed to enable class files to be efficiently verified "off-line" and delivered to the device.
[*]**Handling of Error classes** -- when the Java virtual machine encounters a serious internal problem, it throws an instance of a subclass of java.lang.Error. However, because there is often no reasonable form of programmatic recovery from these errors, a configuration may specify the KVM to halt with a configuration-defined error indication. Or the configuration may allow device vendors to define device-specific behavior and recovery actions when it encounters such conditions.
[*]**Threads and event handling** -- some configurations may require a different application execution model from the standard Java technology-based model using the Thread class and standard event handling.
[*]**Java Native Interface (JNI)** -- many configurations might not need the flexibility of the JNI for the way in which native methods are linked and invoked. A configuration may use a defined alternative, simpler mechanism to invoke native methods.
[*]**Class loaders** -- many configurations might not need the full flexibility of Java class loaders. A configuration must specify the mechanisms by which classes are located and loaded into the KVM.
[*]**Finalization** -- many configurations do not need to support object finalization.
[*]**Maximum size limitations** -- many configurations do not need to support the full range of sizes of internal virtual machine data structures. A configuration may specify a "maximum supported" range for some or all of the following values:[LIST]
[*]The number of classes in a package
[*]The number of interfaces implemented by a class
[*]The number of fields in a class
[*]The number of methods in a class
[*]The number of elements in an array
[*]The number of bytes of code per method
[*]The length of a string in a CONSTANT_UTF8 constant pool entry
[*]The maximum amount of stack that a method may use
[*]The maximum number of locals that a method may use[/LIST] 
[*]**Start-up** -- each configuration must specify how the KVM locates the initial class and method to execute and the expected attributes of that class and method.[/LIST]**The Java2 Micro Edition Core APIs**

The Java 2 Micro Edition specifies a core set of APIs. These are required by all configurations and, therefore, must be supported by all K virtual machines. In addition to this minimum subset, every KVM must also support whatever APIs are specified by its configuration. This is a very prelminary draft of the Java 2 ME APIs. We anticipate adding substantial additional functionality drawn from Java 2 Standard Edition core packages.
 The following list contains only the class names. Many of these classes have been significantly subsetted in order to reduce the minimum required functionality to key fields and methods.
 
**Basic Classes from java.lang**

  Object, Runtime, System These classes are included in the core API because they are fundamental to the operation of the virtual machine. However, because threading is an optional feature, the minimal core Object class does not require the various wait and notify methods. In addition, many methods of Runtime and System are not required.
 
**Throwable Classes from java.lang**

 Throwable, Exception, RuntimeException and all its subclasses. These classes are included in the core API because they are also fundamental to the operation of the virtual machine. More complex methods such as printStackTrace are not required.
 
**Data Type Classes from java.lang**

 Boolean, Byte, Character, Integer, Short, Void These classes are included in the core API because they are fundamental and generally useful to most programmers writing in the Java language. These classes are subsetted to only the most necessary methods and fields.
 
**String Classes from java.lang**

 String, StringBuffer These classes are included in the core API because they are fundamental and generally useful to most programmers writing in the Java programming language. These classes are subsetted to only the most necessary methods and fields.
 
**Miscellaneous Classes from java.lang**

 Math This class is included in the core API because a few of its methods are generally useful to most programmers writing in the Java programming language.
 
**Miscellaneous Classes from java.util**

 BitSet, Dictionary, Enumeration, Hashtable, Vector These classes are included in the core API because they are generally useful to most programmers writing in the Java programming language. 
 
**Optimizations for Consumer Devices**

The KVM technology team had the goal of building a smaller Java technology-based system. We started by building a straightforward, small, and consistently written bytecode interpreter. The developers of the KVM technology took the "blank slate" rather than the "full tablet" approach to building a smaller Java virtual machine. Beginning with the complete JDKTM technology and then removing the parts that were not needed would not have worked well since much of the standard JDK is too big to fit on a memory-constrained platform. Instead, we started with a blank slate and then added only what was absolutely necessary. This approach made it easier for developers on the team to discover dependencies in an incremental fashion and deal with them appropriately. After getting the basic system to run, we started studying space-efficient optimization techniques to improve the performance of the virtual machine. We also started implementing a subset of the libraries that would be compatible with the standard libraries but would have a substantially smaller memory footprint.
 
**Engineering a small footprint core API**

 In order to create a scalable, minimal footprint system, much work has gone into optimizing the implementation of the Java 2 ME core API. The team removed dependencies between classes whenever possible. We also employed a few simple techniques to shrink the class libraries dramatically:[LIST]
[*]Because our implementation is performance-oriented, we removed the option to use alternate forms of functions. For example, String(char[]) is simply a call to String(char[], 0, ). Note that, with smart inlining in a performance-oriented implementation, much of the overhead of these forms is eliminated.
[*]We eliminated seldom-used classes or classes that can be added by the user if necessary, such as ThreadGroup.
[*]We avoided classes that create many short-term objects, such as Point. Instead of using Point objects, we simply used x and y coordinates as parameters.We decided that AWT (because of its size) is not appropriate for all embedded platforms. Instead, we took advantage of native platform support for I/O and graphics.[/LIST]**Design Considerations for the KVM**

Our design goal for the KVM was to have a small memory footprint without loss of performance. Therefore, we implemented around a straightforward bytecode interpreter with some optimizations of the Java virtual machine. The representation of the internal structures is conventional in the sense that each class has a constant pool, method table, field table, and interface table. However, most of the structures have been implemented as linear tables to provide faster access and to conserve memory space. We have also taken advantage of various low-level features of the C programming language to achieve better performance. 
**Portability**

 Portability was another important goal in the KVM design. For this reason, non-portable code elements (including functions that obtain information about the host computing system) have been minimized and limited to a single file. Multithreading and the garbage collector have been implemented in a completely platform-independent fashion. Rather than relying on external interrupts, the multi-tasker performs thread switching on the basis of the number of bytecodes the current thread has executed, making thread switching more deterministic and easier to debug. This approach is practical because we are not targeting multiprocessor platforms. 
**Garbage Collection**

 We provided a simple, non-moving, single-space mark-and-sweep garbage collector. It operates well with heap sizes of just a few tens of kilobytes. The collector is handle-free, because we always used direct rather than indirect object references. 
**Host System Calls**

 To minimize memory usage, we implemented the native functions and wrappers used to call host system functions - which would ordinarily be implemented through the Java Native Interface - by making them a part of the virtual machine. Currently, the native function support is very limited. Graphics are currently implemented by calling platform-specific graphics functions. There is no support for AWT, Project Swing, or any other high-level graphics libraries.
 Another space-reducing tactic was implementing the KVM in C. However, we also minimized the number of C runtime functions that the virtual machine calls in order to ease implementation or replacement of those functions. If any of the debugging modes in the source code are enabled, then the target platform must support the *fprintf* function in the standard C I/O library (*stdio*), or a function with the same interface as *fprintf*.
 
**Conclusion**

 As we move into the future our goal for the KVM technology is to evolve the K virtual machine and to provide tools to accomplish the following goals:[LIST]
[*]Optimize class file format to reduce space requirements and to reduce time to install on the device.
[*]To provide other space and performance optimizations.
[*]To trim other "generally useful" packages (like java.net and java.io) so that they will fit better, and so that profiles can optionally specify them.
[*]To produce a lightweight JNI capable of running on the small footprint of KVM technology.
[*]To produce a KVM capable of supporting consumer JiniTM connection technology client code.
[*]Sun will work with vendors and content providers to develop optimal APIs for a variety of application profiles.
[*]To support application development done on workstations using standard Java development tools. Then, after the code is compiled and a Java technology-based classfile is generated, the classfile would be passed through a converter designed to support the needs of a particular application profile. The converter would optimize the bytecode to fit within the small footprint of an embedded device, and convert bytecode to run in the virtual machine within that embedded device.[/LIST][http://java.sun.com/products/cldc/wp/](http://java.sun.com/products/cldc/wp/)     
    [IMG]http://java.sun.com/im/a.gif[/IMG]

---

### Post by RAV TUX on 2007-01-01
[> ]("http://linuxtracker.org/browse.php?cat=390")[[IMG]http://linuxtracker.org/images/categories/sabayon.png[/IMG]]("http://linuxtracker.org/browse.php?cat=390")  [IMG]http://linuxtracker.org/images/cross.gif[/IMG] [**Sabayon Linux x86-64 3.25 DVD**]("http://linuxtracker.org/torrents-details.php?id=3362&hit=1") 2007-01-02 01:45:21[[IMG]http://linuxtracker.org/images/icon_01.jpg[/IMG]]("http://linuxtracker.org/download.php?id=3362&name=SabayonLinux-x86_64-3.25c.iso.torrent")[URL="http://linuxtracker.org/torrents-nfo.php?id=3362"]
[/URL] [COLOR=green]**LOCAL**[/COLOR]--- [FONT=Verdana][SIZE=1]3.35 GB[/SIZE][/FONT] **Date Added: **2007-01-02 at 01:45:21
**Added By: **[lxnay]("http://linuxtracker.org/account-details.php?id=2221")

 
 
[[IMG]http://linuxtracker.org/images/categories/sabayon.png[/IMG]]("http://linuxtracker.org/browse.php?cat=390")  [IMG]http://linuxtracker.org/images/cross.gif[/IMG] [**Sabayon Linux x86 3.25 DVD**]("http://linuxtracker.org/torrents-details.php?id=3361&hit=1") 2007-01-02 01:06:02[[IMG]http://linuxtracker.org/images/icon_01.jpg[/IMG]]("http://linuxtracker.org/download.php?id=3361&name=SabayonLinux-x86-3.25c.iso.torrent")[URL="http://linuxtracker.org/torrents-nfo.php?id=3361"]
[/URL] [COLOR=green]**LOCAL**[/COLOR]--- [FONT=Verdana][SIZE=1]3.01 GB[/SIZE][/FONT]

[http://linuxtracker.org/torrents-search.php?search=sabayon](http://linuxtracker.org/torrents-search.php?search=sabayon)

---

### Post by mips on 2007-01-02
Grrr, releases are so fast. I will consider downloading this & installing over my existing install.

First wanna hang out in irc & the forums to check if people are reporting common issues.

---

### Post by kazuya on 2007-01-02
Thanks for the Link. My next mission.

---

### Post by Rodneyck on 2007-01-02
Is there a way to just do an update from a 3.2 disk to a 3.25?  I really do not want to download another DVD iso... ](*,)

---

### Post by mips on 2007-01-02
> **Rodneyck said:**
> Is there a way to just do an update from a 3.2 disk to a 3.25?  I really do not want to download another DVD iso... ](*,)

xdelta patches to create a new dvd from your existing one is one way i think.

---

### Post by Rodneyck on 2007-01-02
> **mips said:**
> xdelta patches to create a new dvd from your existing one is one way i think.

Thanks mips.  No, actually, I meant after the 3.2 is installed. Do you just run the updates and it updates you to that version or must you reinstall the whole OS again to get 3.25?  I assume it is like moving from dapper to edgy, or not.  This is my question.

---

### Post by RAV TUX on 2007-01-02
> **Rodneyck said:**
> Thanks mips.  No, actually, I meant after the 3.2 is installed. Do you just run the updates and it updates you to that version or must you reinstall the whole OS again to get 3.25?  I assume it is like moving from dapper to edgy, or not.  This is my question.

 irc.oftc.net

#sabayon

ask...

---

### Post by Rodneyck on 2007-01-02
> **RAV TUX said:**
> irc.oftc.net

#sabayon

ask...

Actually, I just found the answer here...  

[http://www.sabayonlinux.org/forum/viewtopic.php?t=3065&highlight=update+3+25](http://www.sabayonlinux.org/forum/viewtopic.php?t=3065&highlight=update+3+25)

Save yourself some time if you have a previous version disk. You can either use that disk (3.2 or earlier versions) to update (forgot about that feature) OR you can run a command in the link above.

Thx guys.

---

### Post by Rodneyck on 2007-01-03
Well I tried firing up both the mini 3.2 CD and the 3.2 DVD again, installed the mini first. I then tried to update through emerge and got a "masked package" error. Apparently this is a common thing. I tried to look for help, a way around it, but nothing on the forum worked.  This error prohibits any updating unfortunately.

I then decided to install the bloated DVD 3.2 and after trying to update, I got the same error. I gave up. I have no idea why I even try leaving Ubuntu... and after that, I can say that I really, really like synaptic and apt-get. :D

---

### Post by RAV TUX on 2007-01-03
> **Rodneyck said:**
> Well I tried firing up both the mini 3.2 CD and the 3.2 DVD again, installed the mini first. I then tried to update through emerge and got a "masked package" error. Apparently this is a common thing. I tried to look for help, a way around it, but nothing on the forum worked.  This error prohibits any updating unfortunately.

I then decided to install the bloated DVD 3.2 and after trying to update, I got the same error. I gave up. I have no idea why I even try leaving Ubuntu... and after that, I can say that I really, really like synaptic and apt-get. :Dmasked packages are there to protect you from destroying your system.

---

### Post by _simon_ on 2007-01-03
Just downloading the ISO to give it a go.

Has anyone moved from Ubuntu to Sabayon and if so why?

---

### Post by mips on 2007-01-03
> **_simon_ said:**
> Just downloading the ISO to give it a go.

Has anyone moved from Ubuntu to Sabayon and if so why?

Yes, for about a month now. Don't even have (K)Ubuntu anymore on my drives. Rav Tux is another that moved to Sabayon that I know of.

Find it faster & more stable than kubuntu. Also easier to get things working in 64bit than with debian based distros. Everything just works out of the box as well, no need to install any codecs, java etc Comes with the latest nvidia/ati video drivers. The software is also very recent but stable though.

It's a new experience and a bit of a learning curve but well worth it. I installed off the mini-ed cd (3.20) and had a java issue but that was fixed, this would not have happened if i used the DVD.

Btw, there is a script out that reduces the bloated dvd install to the cd install, the script however lives on the mini ed cd.

---

### Post by Down8ve on 2007-01-03
Concerning moving from Ubuntu to Sabayon 3.25, I am considering deleting Sabayon from my drive.

While it does install all the multimedia goodies and Beryl 1.4 without any problem, there are odd pauses and near-freezes that make it unsatisfactory for me.  This erratic behavior of the interface, at least on my hardware, is ruining my Sabayon experience.  The new KDE menu does not work well with the hundreds of apps included on the DVD version, but that is easily corrected.  As a matter of personal taste I am learning that perhaps Gnome is a better alternative for me.

Any of you have comments regarding the KDE vs. Gnome in Sabayon?  Does it provide smoother feedback?

-Scott
2.66ghz Pentium D
1 gig memory
Nvidia 7300GT

---

### Post by Down8ve on 2007-01-03
By the way, Mips, are you using the 64-bit version of Sabayon?  That is an option on my hardware, but I am worried about the multimedia stuff so common in those 64-bit versions.

-Scott

---

### Post by RAV TUX on 2007-01-03
> **mips said:**
> Yes, for about a month now. Don't even have (K)Ubuntu anymore on my drives. Rav Tux is another that moved to Sabayon that I know of.



I use Sabayon as my primary OS. I still use Ubuntu on my older computer.

I moderate both here on ubuntuforums.org and sabayonlinux.org as my signature clearly states.

I honestly believe Sabayon is the best OS in existence.

---

### Post by Down8ve on 2007-01-03
> **RAV TUX said:**
> I use Sabayon as my primary OS. I still use Ubuntu on my older computer.

I moderate both here on ubuntuforums.org and sabayonlinux.org as my signature clearly states.

I honestly believe Sabayon is the best OS in existence.

Now that sounds like a ringing endorsement!

Rav, perhaps I should bear with Sabayon a bit longer, maybe look to see what services and login start-ups I don't need before making a hasty judgment.  We'll take a look later today when I have a chance.


-Scott

---

### Post by mips on 2007-01-03
> **Down8ve said:**
> By the way, Mips, are you using the 64-bit version of Sabayon?  That is an option on my hardware, but I am worried about the multimedia stuff so common in those 64-bit versions.

-Scott

Yes I use the 64bit version. So far all my multimedia works. I have 32bit firefox-bin installed that uses flash9. Occassionally I get freezes with this, I dunno whether it is the flash version or the browser. In future i would like to try 64bit firefox with the wrapper for flash stuff.

Your multimedia should work out of the box without hassles.

I have not tried the 32bit sabayon version so i cannot really compare the two. What i can however say is that 64bit is much easier in gentoo based distros compared to debian based distros. I have come across one package so far that was not available for 64bit but it's an obscure one anyway.

---

### Post by Rodneyck on 2007-01-03
> **RAV TUX said:**
> masked packages are there to protect you from destroying your system.

Yes, that is all well and good, but it also prevents you from updating/upgrading your system.  I guess my alternative is to download the 3.25c after all. Still seems like a problem to me.

To answer the gnome on Sabayon question above. I have posted elsewhere that my gnome experience from the DVD 3.2 install was not a very good one. Sabayon is really built and focused around KDE, even though it offers several other front ends.

Under Gnome, many applications behaved erratically, for example, all the word processing programs (abiword, open office writer, etc) would not spell check even though the function was active. You could only use Kuroo once and then it would never return until you rebooted your system. Much of the support is for KDE on the forums and people are generally clueless re anything Gnome. My advise is to stick with KDE on Sabayon until it has baked awhile in the oven and there is more Gnome support.

Is it the best OS? My vote is still undecided. I really hate their updating system (emerge), for me, the one BIG drawback of Sabayon that would make it #1, that, and the KDE thing (not a big fan of KDE.)  What it does have going for it that makes it shine above all other distros is the fact it uses the latest and greatest builds and so more hardware just works with it. My old web camera which has never worked under any other distro, works under Sabayon out of the box. The distro also has a fast release schedule, always updating. This can be both good and bad. Even though they sport a beta testing team, it leaves very little room and time for tackling all the issues. Still, it is nice to have the latest to work with and test.

I would say, if you are the type that needs a stable, reliable system for work and serious productivity, to give Sabayon a pass. If you are the type that loves to fiddle, stays on the cutting edge, not worried if a few apps or problems occur, and have patients for the dreaded Emerge updating system, then give it a go.

---

### Post by dxxvi on 2007-01-03
Well, all this news makes me want to give Sabayon a try (not a go though). I'm happy with my Edgy except the beryl thing (I can't make it run on my Inspiron 8600 nvidia GeForce FX 5200 32MB although my Dapper worked with compiz before :(). 

The main things I work on in Linux is Java (which won't be a problem on Sabayon), Oracle Database 10g Express Edition and Oracle SQL Developer (which are in deb and rpm formats only). So, is there any way to install those Oracle things in Sabayon?

---

### Post by compres on 2007-01-03
Well I have to say I have switched from Kubuntu to Gentoo to Sabayon in a 2 month interval.  

Right now I am staying with Sabayon.  I have to say it's the best I have used becouse it's basically a pre-configured Gentoo. 

Everything just works, and after you install in like 25 minutes total, since it's Gentoo, you can just optimize your whole system.  

In my case, as I am currently broke and studying, I have to live with a p3 1ghz and 256MiB of ram laptop and the optimizations let me run beryl on this system with no slowdown.

Can't say that about Kubuntu...

So basically yes, Sabayon works for me and I am not looking back.

---

### Post by Down8ve on 2007-01-03
Our mileage does vary, no?

Sabayon was installed on my ECS 945G-M3/Pentium D/Nvidia 7300 twice and had various quirks that took the shine off all the colors and a solid Beryl.

I've gone back to having OpenSuSE 10.2, Ubuntu 6.10/Automatix and Win XP.  So far I am enjoying SuSE most of all.  It is smooth, solid and feels like a Lexus in comparison.

Ubuntu still has 200 gigs of my first drive.  It is by far more easy to install and maintain for regular Joes like myself.

---

### Post by rsambuca on 2007-01-04
3.25 doesn't work on my system.  During boot-up from the live DVD (both 32 and 64 bit versions), it gets to a stage and then can't boot as it doesn't recognize a bootable device.  According to lxnay I am out of luck with 3.25 as there is some weird PATA/SATA??? or something-or-other recognition problem of some ide chipsets or something.

3.2 worked for the most part, but still too buggy for me.  Guess I'll have to wait for 3.3!

---

### Post by mips on 2007-01-04
> **rsambuca said:**
> According to lxnay I am out of luck with 3.25 as there is some weird PATA/SATA??? or something-or-other recognition problem of some ide chipsets or something.

3.2 worked for the most part, but still too buggy for me.  Guess I'll have to wait for 3.3!

Yes, there is some new software/system for hard drives.

Maybe pass the dvd's on to someone else that can use them and wait for 3.3, it's suppose to be good but lets not start any hype ;)

---

### Post by compres on 2007-01-05
> **rsambuca said:**
> 3.25 doesn't work on my system.  During boot-up from the live DVD (both 32 and 64 bit versions), it gets to a stage and then can't boot as it doesn't recognize a bootable device.  According to lxnay I am out of luck with 3.25 as there is some weird PATA/SATA??? or something-or-other recognition problem of some ide chipsets or something.

3.2 worked for the most part, but still too buggy for me.  Guess I'll have to wait for 3.3!

I believe those issues have something to do with the new 2.6.19 kernel, maybe for 3.3 they change to a .20 kernel, not sure.

---

### Post by mips on 2007-01-06
> **compres said:**
> I believe those issues have something to do with the new 2.6.19 kernel, maybe for 3.3 they change to a .20 kernel, not sure.

The changes you are referring to were actually backported from .20 to .19 if I recall correctly.

---

### Post by Rodneyck on 2007-01-06
FYI.... Sabayon Linux 3.26: scheduled for tomorrow...

It is mostly bug fixes before they head into v3.3.

---

### Post by rai4shu2 on 2007-01-07
I just tried out the Live DVD 3.25, and it's pretty impressive. I'll definitely have to take another look at KDE.

---

### Post by kazuya on 2007-01-10
I used to use both Ubuntu and Zenwalk. Ubuntu is great, but for some odd reason, after upgrading to edgy and using that for almost a month, on one of my upgrades, I lost my internet. Should be an easy thing to fix, but I could not. I asked for help and read some wiki. Last night I made the switch to Sabayon 3.25. Wow, wow, is all I can say. And the updating of certain apps actually worked via kuroo. It was long though. 

Beryl on Sabayon is unmatched by almost any other distro I have ever used except maybe zenwalk.

Moreover, Sabayon does not feel as bloated with everything, DE installed on my PC. This won me over. I agree though that there is a need to fully polish and make easy the upgrade or installing option via the gui {kuroo}

Installation was very easy and straight-forward. Ubuntu is also great. But this distro does stuff as easily as Ubuntu but with more speed and beauty.

Time will tell though.  I am fully on Sabayon now. I shall triple boot in the future b/w Sabayon, Ubuntu, and maybe Windows XP{for certain avid fans of win that have to play new games for windows.} 

I use XP only in the office as I have no choice. But once I start working from home. That may come to an end.

EDIT: Zenwalk 4 is still my favorite OS. And I am now using both as my primary OSes. Zen simply flies. Sabayon on the otherhand is beautiful.

---

### Post by bvanaerde on 2007-01-15
A few days ago, I tried out Sabayon 3.26.
The LiveCD went really smooth, I selected desktop acceleration with Xgl (because of my Ati 9800 pro).

I was really happy with it, so I decided to install it.
For some reason, everything was so slow. Xgl was contstantly using about 80% of my processor, and Beryl wasn't even used at startup.

I might do a fresh install next weekend to try again...

---

