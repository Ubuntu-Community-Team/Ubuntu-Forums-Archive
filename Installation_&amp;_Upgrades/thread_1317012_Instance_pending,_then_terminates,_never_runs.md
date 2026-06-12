---
title: "Instance pending, then terminates, never runs"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ewgates on 2009-11-06
[FONT=Courier New][SIZE=3]I am currently trying to run an instance on an Ubuntu 9.10 Server with Eucalyptus cloud. Before that, I was trying to run an instance on Ubuntu 9.04 with Eucalyptus cloud installed by hand with the same results. **The instances show pending, sometimes for hours, before terminating.** I have never seen a running state. I would appreciate any feedback at all.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]The Ubuntu install disc was created on Monday morning 2Nov09.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]During the installation, I followed the UEC/CDInstall document found at [/SIZE][/FONT][[FONT=Courier New][SIZE=3]https://help.ubuntu.com/community/UEC/CDInstall[/SIZE][/FONT]]("https://help.ubuntu.com/community/UEC/CDInstall")[SIZE=3][FONT=Courier New] . [/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]The setup is two Dell E6400 laptops, one as the Cloud and CC (hostname cloud1, IP=192.168.2.226), the other as the Node (hostname cloud3, IP=192.168.2.212). [/FONT][/SIZE]
 
[FONT=Courier New][SIZE=3]VT selections in the BIOS of the laptops are set.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]Eucalyptus on the CC can SSH into eucalylptus on the NC without passwords.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]The image is the “Ubuntu 9.10 RC – Karmic Koala (amd64) Image Version 20091022” installed from the eucalyptus login, “store” menu. The only user is admin.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]On my latest installation attempt, I ran “euca-run-instances emi-DEE31066 –k mykey –t m1.xlarge –n 1-4” , it remained pending then terminated without going into the running state. In the logs it is run on 05Nov09 at 3:47pm.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]I also ran “euca-run-instances emi-DEE31066 –k mykey –t c1.medium –n 1-4” on this and previous installations this week, with the same results. The c1.medium run looked like it was creating two instances at 192.168.2.100 and 192.168.2.101.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]During previous installs this week, using Ubuntu 9.10 Server with Eucalyptus cloud, I saw the same issues, but tried various solutions found online. [/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]In this last install, I setup the partitions to include entire disk with LVM, but previous installs this week simply specified entire disk without LVM because I don’t think I need LVM.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]During installation specified no email, because I plan to run all instances as admin.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]One observation, when I run “euca-describe-availability-zones verbose”, I do see the cluster name with IP, and the instance sizes, but no nodes are listed. There are no nodes listed in the UEC/CDInstall example either but other documents state that the nodes should be listed.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]From the logs, it does look like the CC and NC are communicating, and the NC is communicating with Walrus.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]I am pretty confident that the keys and certifications match properly between the front end and node. One observation is that I see, in the cc.log file, the following ssh key:[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]([http://192.168.2.212:8775/axis2/services/EucalyptusNC](http://192.168.2.212:8775/axis2/services/EucalyptusNC)) running instance: i-4A950821 emi-DEE31066 d0:0d:4A:95:08:21 d0:0d:4A:95:08:21 10 ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCA+qIIDTjfIWfOXe7aNNKdTGZKXisgRXZU2fFEyA3FIJqBbRNlrz2tF8mnBWvK2k4KgnQDLrod989K+3CHHxwZRIJ8Zt3b8rg4z5MVMTdknSN3I7754BTqaQACWIq6ymADYEnFKBCi0QueAEdLELfMyMOLnvyyVD/hKVL8SEAAkrGBqNnmR3yfs8JutjsgjBzupanXwkEKm2SdHyZY66rh3kxBCwzJ/JGwoonpVXfVj4lsH4DNUQ+kAOjn3ZjhlJZA5mwnNiW7GyCTilk0UPjFny0SQDI+GDTHxktgoSBrQl7tRgoLrSVySY42KUQ59Q+4wFhR/yUz4gLv/dG/RkqP admin@eucalyptus[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]But the nodes ~/eucalyptus/.ssh/authorized_keys shows an ssh-rsa ending with “EAo1E1mPRQ== eucalyptus@cloud1” which matches the front end’s .ssh/id_rsa.pub when logged in as eucalyptus@cloud1.[/SIZE][/FONT]
 
[SIZE=3][FONT=Courier New]The nc.log shows the error “[FONT=Courier New]libvirt: Domain not found: no domain with matching name 'i-4A950821' (code=42)”[/FONT][/FONT][/SIZE]
 
[FONT=Courier New][SIZE=3]The node’s euca_test_nc.log shows no errors.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]The command “virsh –c qemu:///system list” does show a connection on the node.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]My first installation of ubuntu 9.10 server with eucalyptus cloud was an upgrade from ubuntu 9.04 desktop. One online user’s solution to a similar problem (defect #461186) was to install the cluster (front end) ubuntu 9.10 server on a laptop that had not been previously installed with Ubuntu. The current installation is a laptop that has only been installed with ubuntu 9.10 server with cloud. The node is an upgrade from 9.04 ubuntu desktop (I had attempted to install eucalyptus by hand) to 9.10 ubuntu server with cloud. I simply ran out of laptops. [/SIZE][/FONT]
 
[SIZE=3][FONT=Courier New]The cc.log file shows the following errors/warnings grouped together: [/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]“[FONT=Courier New]bad input params to vnetAttachTunnels()”[/FONT][/FONT][/SIZE]
[FONT=Courier New][SIZE=3]“failed to attach tunnels for vlan 10 during maintainNetworkState()”[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]“network state maintainance failed”[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]“in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled”[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]The bridge setup in the node is the default when ubuntu 9.10 server with cloud was installed.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]I can supply all or part of the nc.log and cc.log files.[/SIZE][/FONT]

---

### Post by jon_herr on 2009-11-08
Same exact problem here...

Spent hours trying to figure this one out. 

Anyone?  Is there a "cloud" person in the house?


FYI:  I was able to prolong the pain by increasing the size of the allocated drive space for VMs...  but this resulted in the machine being declared "running" for a few seconds before termination.

Termination cause is stated to be "user requested shutdown" - which is not true.  This user is requesting that things work!  This user is probably making a simple mistake but I am new to Clouds and don't know where to start...

---

### Post by vovantics on 2009-11-09
I too am seeing this error in the cc.log:
"in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled"

> Is this expected? I installed the node using the Ubuntu 9.10 Server ISO.


Here's where I'm at. I was able to install the "Ubuntu 9.10 RC - Karmic Koala (i386)" image via the Eucalyptus controller web interface.
I'm also able to view my installed image via ElasticFox. The problem occurs when I try to instantiate an instance from ElasticFox. 

Here's the error in cloud-error.log:
Payload               : edu.ucsb.eucalyptus.cloud.VmAllocationInfo@1373194
JavaDoc               : [http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html](http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html)
********************************************************************************
Exception stack is:
1. Not enough resources: vm resources in the requested cluster clustertest (com.eucalyptus.util.EucalyptusCloudException)
  edu.ucsb.eucalyptus.cloud.ws.VmAdmissionControl:120 (null)
2. Component that caused exception is: FinishedVerify. Message payload is of type: VmAllocationInfo (org.mule.api.service.ServiceException)
  org.mule.component.DefaultLifecycleAdapter:214 ([http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html](http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html))
********************************************************************************
Root Exception stack trace:
com.eucalyptus.util.EucalyptusCloudException: Not enough resources: vm resources in the requested cluster clustertest
        at edu.ucsb.eucalyptus.cloud.ws.VmAdmissionControl.evaluate(VmAdmissionControl.java:120)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.mule.model.resolvers.AbstractEntryPointResolver.invokeMethod(AbstractEntryPointResolver.java:147)
        at org.mule.model.resolvers.ReflectionEntryPointResolver.invoke(ReflectionEntryPointResolver.java:127)
        at org.mule.model.resolvers.DefaultEntryPointResolverSet.invoke(DefaultEntryPointResolverSet.java:50)
        at org.mule.component.DefaultLifecycleAdapter.intercept(DefaultLifecycleAdapter.java:202)
        at org.mule.component.AbstractJavaComponent.invokeComponentInstance(AbstractJavaComponent.java:82)
        at org.mule.component.AbstractJavaComponent.doOnCall(AbstractJavaComponent.java:73)
        at org.mule.component.AbstractComponent.onCall(AbstractComponent.java:87)
        at org.mule.model.seda.SedaService$ComponentStageWorker.run(SedaService.java:533)
        at org.mule.work.WorkerContext.run(WorkerContext.java:310)
        at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1061)
        at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:575)
        at java.lang.Thread.run(Thread.java:636)

********************************************************************************

> Can someone tell me what "Not enough resources: vm resources in the requested cluster clustertest" means?

---

### Post by ewgates on 2009-11-09
I installed and downloaded the 32bit version of the Ubuntu 9.10 RC image.  Then executed "euca-run-instances emi-E22D108D -k mykey -t c1.medium -n 1-4" which is now in a running state.
 
It looks like the 64bit version will not run on my 64 bit machine but the 32bit version will.  I have not yet determined why.  I do have a running instance.  Yay!

---

### Post by jon_herr on 2009-11-09
Did you install the 64 bit version of "server" or 32?

---

### Post by ewgates on 2009-11-09
It is the 64bit version.

---

### Post by jon_herr on 2009-11-09
K, thanks.

I just tried i386 version with the same results...  goes from pending, running, terminated.  

Reason:  "user requested shutdown"

Which is not true...

"user requests that this start working!"

---

### Post by jon_herr on 2009-11-09
Okay,
So after I turned on hardware virturalization support the machine came up and stayed up.

Shouldn't have to do that but I did...

Now what do I do?  The machine is running but I can't connect to it...  I must be missing something else?

I can see it's status from elasticfox...  but when I right click and say connect to instance I'm prompted for a key and then nothing happens.  I've also tried to ssh in to the session using the ip address that the instance has been given but nothing happens.

FYI: the IP subnet is different from my 'normal' network 192.168.15.x for cloud, 192.168.0.x for my 'normal' real network.  

I've manually set the connecting machine to the same network at 192.168.15.x - but still can't connect.

Thanks,
Jon

---

### Post by ewgates on 2009-11-10
Once my instance started running, I had no trouble using ssh to get into it.
 
On my front end (cloud + cluster controller) I found the IP address of the instance.
The command  "euca-describe-instances" will provide IP-of-instance.
 
Then I connected.
  "ssh -i ~/.euca/mykey.[COLOR=black]priv [/COLOR][EMAIL="ubuntu@IP-of-instance"][COLOR=black]ubuntu@IP-of-instance[/COLOR][/EMAIL]"

---

### Post by peter.w on 2009-11-30
Same problem with Ubuntu 9.10 Cloud.
Instance first is in "pending" status, then few secs - "running" and then "terminated".
Did somebody find solution - seems to be mainstream bug..?

---

### Post by ewgates on 2009-11-30
[COLOR=black][FONT=Verdana]I have managed to keep a simple cloud instance running for over a week.    I didn't find a solution so much as a work around.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have the two Del E6400 laptops, one setup as the front end with the cloud and cluster controller, the other setup as the node with the node controller.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Both have ubuntu 9.10 32bit server installed with cloud.  I followed the install instructions "UEC/CDInstall" from the Community Ubuntu Documentation and kept the setup as simple as possible.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I then installed the ubuntu desktop on the front end.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I then downloaded and installed the 32bit ubuntu image from the Ubuntu Enterprise Cloud web login.  The only account is the admin account.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I then ran the instance specifying a large size.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]In order to install java on the instance, I SSHd into it and modified the sources.list file to include the deb resources needed to install java.  Then I installed java.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I haven't done anything else with it in the last week or so.  I've been working on other tasks.  But the instance is still running, which is a first.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I couldn't get any other combination of ubuntu or image to run for long.  The key for me is 64bit machine, 32bit 9.10 ubuntu server with cloud, 32bit canned image.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]You will find a total of three forum issues that I have submitted under user "ewgates".  They might be helpful too.  [/FONT][/COLOR]

---

### Post by ionz on 2009-12-04
> **peter.w said:**
> Same problem with Ubuntu 9.10 Cloud.
Instance first is in "pending" status, then few secs - "running" and then "terminated".
Did somebody find solution - seems to be mainstream bug..?


Same here but I never see the running portion haha... just pending to terminated
But I since I was experimenting I used Xen VM's for the Controller and Nodes.  All of them are running 32bit 9.10 including the instance.  VT is enabled on the hypervisor but I dont think it's inherited because the nodes complained at install.    I guess I should try out physical machines with VT.

---

### Post by sonoffett on 2010-01-06
I am having this same problem, running the VMs in software (my servers don't have VT). Was anyone able to work around this without resorting to hardware?

---

### Post by mithil on 2010-02-01
Same problem here..
However, the karmic server(32-bit) instance remains in running state BUT cannot connect to the instance using elasticfox.Also 'ssh' into the instance not possible.
               Cloud is on the same network as that of LAN and so are the instances, but it is not possible to 'ping' into the instance from a client PC. However 'ping' works fine from the front-end machine(CLC,CC,SC,Walrus).
                When the running instance is terminated, it cannot reboot..(Error:cannot find the object!)

Any help is greatly appreciated!
mithil.

---

### Post by ripeart on 2010-02-07
I have the same issue. I started with two Thinkpad tablets running 9.10, one is basically everything (cc,sc,walrus) the other is simply a node controller. Additionally, I had 4 x G4 (PPC) mac cubes laying around so I installed 9.04 minimal on them and (long story) eventually got eucalyptus-nc and libvirt up and running on them. I have been able to get a) the thinkpads running first, then b) with much effort I was able to configure and add each of the cubes to the cluster (long story, but once I was successful with one, I repeated the steps for the other three). However I don't really know if they are actually doing anything. Running 'top' on them doesn't show eucalyptus much, however 'top' on the Thinkpads definitely shows that eucalyptus is using resources. Is there a command to verify that nodes are connected and actually taking traffic/crunching data?  

I suppose my main concern at this point is to know if there is a way to determine if my node controllers are actually contributing horsepower to the cloud. After ssh sync, the 'euca_conf -addnode' command has been successful on each node however I would like to have **empirical** proof of their contribution.

Anyway, I have the same problem as others where I instantiate 9.10 via the cli however it floats in 'pending' for a few minutes, then just terminates because "user requested shutdown".

I really want to get this working.

---

### Post by lifelessr on 2010-02-10
I had very similar symptoms, I found two problems:
[https://bugs.edge.launchpad.net/ubuntu/+source/eucalyptus/+bug/519648](https://bugs.edge.launchpad.net/ubuntu/+source/eucalyptus/+bug/519648)
[https://bugs.edge.launchpad.net/ubuntu/+source/eucalyptus/+bug/519653](https://bugs.edge.launchpad.net/ubuntu/+source/eucalyptus/+bug/519653)

The first was missing pem files for the nc service so it wasn't registering properly (this causes the insufficient vms - 0 instances available in euca-describe-availability-zones --verbose

The second caused the disk image caching and deployment for the nc service to fail - missing a few key directories matters a lot.

Now I have the instances coming up but timing out waiting for the metadata service ><.

---

### Post by lifelessr on 2010-02-10
I'm all sorted - turns out that the PUB and PRIV interfaces were set to eth0, not br0, and this causes epic fails when the machine's networking is configured on br0 :). Also there is a patch to load iptables earlier which makes the various UEC servers talk to each other a lot more happily. [https://bugs.edge.launchpad.net/ubuntu/+source/eucalyptus/+bug/503180](https://bugs.edge.launchpad.net/ubuntu/+source/eucalyptus/+bug/503180) has that patch.

---

### Post by rogue780 on 2011-01-14
Did you turn on hardware virtualization in hte BIOS or is it an Eucalyptus option? I'm having the same problem that you were describing, but I know for a fact that virtualization is enabled on the hardware side, I just don't know if there's some software side that I need to worry about. The server I've got is running on AMD opterons.

---

