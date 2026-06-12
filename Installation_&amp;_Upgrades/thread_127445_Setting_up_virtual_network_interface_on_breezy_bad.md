---
title: "Setting up virtual network interface on breezy badger"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by azolkipl on 2006-02-08
Hello all,

I'm currently running an OS simulator on a breezy badger box. The network portion of the simulator will use the eth0 interface and completely render the workstations own networking useless. To overcome this issue, I plan to use a virtual interface (tap0) and bridge it to the eth0 interface. I tried using ethertap and brctl to try and resolve this issue. But it seems either I'm doing something wrong, or ethertap is not supported in the 2.6 kernel anymore.

Can somebody please tell me how do I go about making a virtual interface on breezy badger? FYI, the simulator is a proprietary OS sim, so it's not qemu or vmware or any of the other virtual PC type of software that auto creates interfaces for you.

this is essentially what i want to do:

 ______		      ______		   ______
 |	|		<	>		|	|
 |tap0|=======<   br0	 >=======|tap1	|
 |	|		<	>		|	|
 ------		       -------		    --------
		    	   ||
		    	   ||
		    	   ||
 		  	______
		 	/	\
 		 	| eth0|
 		 	\	/
 		 	 ------

Any help would be appreciated.

Thanks

---

