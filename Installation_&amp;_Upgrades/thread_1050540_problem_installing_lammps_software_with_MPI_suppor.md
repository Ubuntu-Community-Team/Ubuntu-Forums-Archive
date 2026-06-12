---
title: "problem installing lammps software with MPI support"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by oscar78 on 2009-01-25
So I have been struggling for the past few days to install a simulation package lammps ([http://lammps.sandia.gov/](http://lammps.sandia.gov/)) on my Mac OS X.  I am well aware that this is a Ubuntu forum, but you guys seem to know a lot of UNIX stuff, so I was hoping someone might have a solution to my problem...

To run lammps on parallel processors, I have installed the Message Passaging Interface package, MPICH.  The problem is that when compiling lammps, it doesn't recognize library elements from MPICH, giving me the following error output:

-------------------------------------------------------------
g++ -g -O -L/Users/andy/mpich/mpich2-install/lib angle.o angle_charmm.o angle_cosine.o angle_cosine_delta.o angle_cosine_squared.o angle_harmonic.o angle_hybrid.o atom.o atom_vec.o atom_vec_angle.o atom_vec_atomic.o atom_vec_bond.o atom_vec_charge.o atom_vec_full.o atom_vec_hybrid.o atom_vec_molecular.o bond.o bond_fene.o bond_fene_expand.o bond_harmonic.o bond_hybrid.o bond_morse.o bond_nonlinear.o bond_quartic.o change_box.o comm.o compute.o compute_centro_atom.o compute_coord_atom.o compute_displace_atom.o compute_erotate_sphere.o compute_group_group.o compute_ke.o compute_ke_atom.o compute_pe.o compute_pe_atom.o compute_pressure.o compute_reduce.o compute_stress_atom.o compute_temp.o compute_temp_com.o compute_temp_deform.o compute_temp_partial.o compute_temp_ramp.o compute_temp_region.o compute_temp_sphere.o create_atoms.o create_box.o delete_atoms.o delete_bonds.o dihedral.o dihedral_charmm.o dihedral_harmonic.o dihedral_helix.o dihedral_hybrid.o dihedral_multi_harmonic.o dihedral_opls.o displace_atoms.o displace_box.o domain.o dump.o dump_atom.o dump_bond.o dump_custom.o dump_dcd.o dump_xyz.o error.o ewald.o fft3d.o fft3d_wrap.o finish.o fix.o fix_add_force.o fix_ave_atom.o fix_ave_force.o fix_ave_spatial.o fix_ave_time.o fix_bond_break.o fix_bond_create.o fix_bond_swap.o fix_com.o fix_coord_original.o fix_deform.o fix_deposit.o fix_drag.o fix_dt_reset.o fix_efield.o fix_enforce2d.o fix_gravity.o fix_gyration.o fix_heat.o fix_indent.o fix_langevin.o fix_line_force.o fix_minimize.o fix_momentum.o fix_msd.o fix_nph.o fix_npt.o fix_npt_sphere.o fix_nve.o fix_nve_limit.o fix_nve_noforce.o fix_nve_sphere.o fix_nvt.o fix_nvt_sllod.o fix_nvt_sphere.o fix_orient_fcc.o fix_plane_force.o fix_press_berendsen.o fix_print.o fix_rdf.o fix_recenter.o fix_respa.o fix_rigid.o fix_set_force.o fix_shake.o fix_shear_history.o fix_spring.o fix_spring_rg.o fix_spring_self.o fix_temp_berendsen.o fix_temp_rescale.o fix_thermal_conductivity.o fix_tmd.o fix_viscosity.o fix_viscous.o fix_wall_lj126.o fix_wall_lj93.o fix_wall_reflect.o fix_wiggle.o force.o group.o improper.o improper_cvff.o improper_harmonic.o improper_hybrid.o input.o integrate.o kspace.o lammps.o lattice.o library.o main.o memory.o min.o min_cg.o min_sd.o minimize.o modify.o neigh_bond.o neigh_derive.o neigh_full.o neigh_gran.o neigh_half_bin.o neigh_half_multi.o neigh_half_nsq.o neigh_list.o neigh_request.o neigh_respa.o neigh_stencil.o neighbor.o output.o pack.o pair.o pair_airebo.o pair_buck.o pair_buck_coul_cut.o pair_buck_coul_long.o pair_coul_cut.o pair_coul_debye.o pair_coul_long.o pair_eam.o pair_eam_alloy.o pair_eam_fs.o pair_hybrid.o pair_hybrid_overlay.o pair_lj_charmm_coul_charmm.o pair_lj_charmm_coul_charmm_implicit.o pair_lj_charmm_coul_long.o pair_lj_cut.o pair_lj_cut_coul_cut.o pair_lj_cut_coul_debye.o pair_lj_cut_coul_long.o pair_lj_cut_coul_long_tip4p.o pair_lj_expand.o pair_lj_gromacs.o pair_lj_gromacs_coul_gromacs.o pair_lj_smooth.o pair_morse.o pair_soft.o pair_sw.o pair_table.o pair_tersoff.o pair_tersoff_zbl.o pair_yukawa.o pppm.o pppm_tip4p.o random_mars.o random_park.o read_data.o read_restart.o region.o region_block.o region_cylinder.o region_intersect.o region_prism.o region_sphere.o region_union.o remap.o remap_wrap.o replicate.o respa.o run.o set.o shell.o special.o temper.o thermo.o timer.o universe.o update.o variable.o velocity.o verlet.o write_restart.o -lfftw -lfmpich -lmpich -L/sw/lib/ -lg2c -g77libs -lpthread  -o ../lmp_g++test3
/usr/libexec/gcc/i686-apple-darwin8/4.0.1/ld: Undefined symbols:
_MPI_Bcast
_MPI_Allreduce
_MPI_Scan
_MPI_Barrier
_MPI_Cart_create
_MPI_Cart_get
.
.  + a whole bunch more...
.
_MPI_Allgather
_MPI_Comm_dup
_MPI_Waitany
collect2: ld returned 1 exit status
-------------------------------------------------------------
  
The lammps source files contain variables such as 

MPI_Bcast 

with no initial underscore. In investigating this, I've found that the problem lies in the fact that MPICH was compiled using a fortran compiler (g77), but lammps uses g++.  I was told it might be possible to create a separate library to translate between the two types, but do not have much experience in doing so. Does anyone see a resolution to this problem?   

Thanks.

---

