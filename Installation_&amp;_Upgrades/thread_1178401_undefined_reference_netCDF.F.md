---
title: "undefined reference netCDF.F"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by javier.reggae on 2009-06-04
Hello all,  
 

 I am trying to compile and Install the Software Column Radiation Model (CRM) for scientific atmospheric applications.Iam using UBUNTU 9.04. 

 Originally the code use the PGF90 compiler, I am trying to make the translation to gfortran.  
 I am having some troubles:
 

 gfortran-4.4 -o ../bin/crm ../obj/crm.o ../obj/netcdf.o ../obj/endrun.o ../obj/freemem.o ../obj/getmem.o ../obj/blkdat.o ../obj/resetr.o ../obj/orb.o ../obj/albocean.o ../obj/aermix.o ../obj/cldefr.o ../obj/cldems.o ../obj/fmrgrid.o ../obj/radabs.o ../obj/radclr.o ../obj/radclw.o ../obj/radcsw.o ../obj/radctl.o ../obj/radded.o ../obj/radems.o ../obj/radini.o ../obj/radinp.o ../obj/radoz2.o ../obj/radtpl.o ../obj/torgrid.o ../obj/trcab.o ../obj/trcabn.o ../obj/trcems.o ../obj/trcmix.o ../obj/trcplk.o ../obj/trcpth.o ../obj/zenith.o ../obj/intmax.o ../obj/isrchfgt.o ../obj/isrchfle.o ../obj/wheneq.o ../obj/whenfgt.o ../obj/whenflt.o ../obj/whenne.o   -L/usr/lib -lnetcdf  
 ../obj/netcdf.o: In function `nc_err_exit__': 
 netcdf.F:(.text+0xa2): undefined reference to `nf_strerror__' 
 ../obj/netcdf.o: In function `netcdf_': 
 netcdf.F:(.text+0x146): undefined reference to `nf_create__' 
 netcdf.F:(.text+0x170): undefined reference to `nf_def_dim__' 
 netcdf.F:(.text+0x19a): undefined reference to `nf_def_dim__' 
 netcdf.F:(.text+0x1d7): undefined reference to `nf_def_var__' 
 netcdf.F:(.text+0x214): undefined reference to `nf_def_var__' 
 netcdf.F:(.text+0x251): undefined reference to `nf_def_var__' 
 netcdf.F:(.text+0x28e): undefined reference to `nf_def_var__' 

 collect2: ld returned 1 exit status 
 make: *** [crm] Error 1 
 

 someone know how to solve this ??
 I was read a lot of post with similar errors, and I think that this is linkage problem, but I couldn't solve it.
 

 Really I will appreciate your help,  
 

 thanks in advance...  
 Javier.

---

