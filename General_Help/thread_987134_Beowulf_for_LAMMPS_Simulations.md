---
title: "Beowulf for LAMMPS Simulations"
date: 2008-11-19
forum: General Help
---

### Post by ChaosCon on 2008-11-19
Hey everyone-

I work in a theoretical physics lab at a university, and we're interested in setting up a Beowulf cluster with our old machines.  It would primarily be used for molecular dynamics simulations using [LAMMPS]("http://lammps.sandia.gov/").  We have four spare machines that would form the foundation of the cluster, plus a Ubuntu server running as the main repository of the lab.  Might anybody have any suggestions/tips/links as to how to do this?  Thanks in advance!

~Connor

---

### Post by Claus7 on 2009-06-26
Hello,

as they say in the Lammps site, the compilation of the package might be non trivial. It depends on whether you want to install it in parallel or sequentially. The best site you can start of is the lammps web site. 
Now for the server it is really a difficult task. You have to have good knowledge of what you want to do in order to achieve a good performance. The amount of the machines is irrelevant somehow, as the configuration is practically the same as you add more machines. The thing is that the machines you add should be more or less identical for better performance. 

Your question is really very broad. What I would start with is solving one problem at a time. For example if you want a Beowulf cluster, then you have to have in mind that one machine would be your primary node (master) and the others would be your ordinary nodes. 

So, you have to build the operating system of your cluster and establish a good communication with the nodes and then bother for the installation of the packages.

Regards!

---

