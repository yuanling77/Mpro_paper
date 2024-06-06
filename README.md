Here are the input files for the simulations, molecular dynamics simulation steps, and the script for the contact map as described in the paper "Computational insights into SARS-CoV-2 main protease mutations and nirmatrelvir efficacy: the effects of P132H and P132H-A173V".

1.	Molecular Dynamics Simulations
The Binding_energy folder contains three subfolders: WT-Amber, P132H-Amber, and P132H-A173V-Amber, which are used for the molecular dynamics simulations and MM-GBSA calculations based on the simulation trajectories for WT, P132H, and P132H-A173V, respectively. In each subfolder, the input files for molecular dynamics simulations are located in replicaX. You only need to run the md_run.py script to automatically perform molecular dynamics simulations for 10 replicas.

2.	Binding Free Energy Calculations
Following the method described in the paper, extract the equilibrium trajectories from each molecular dynamics simulation, concatenate them into a trajectory XX.mdcrd, and run MMPBSA.py -O -i mmpbsa.in -sp Mpro-4wi_solvated.prmtop -cp Mpro-4wi.prmtop -rp Mpro.prmtop -lp 4wi.prmtop -y XX.mdcrd to obtain the binding free energy.

3.	Reaction Free-Energy Profile Calculations
The Binding_energy folder contains three subfolders: WT-Q, P132H-Q, and P132H-A173V-Q, which are used for the EVB calculations for WT, P132H, and P132H-A173V, respectively. The input files and parameters are located in input_files. First, run the evb_input_produce.py script to generate 40 folders for repeated EVB calculations. Then, run the total-run.py script to perform the EVB calculations. After the EVB calculations are completed, run the activation_energy_Q1.py and activation_energy_Q2.py scripts to obtain the free energy of each state (TS1, PS1, TS2, PS2).

4.	Contact Map
Based on the concatenated trajectory XX.mdcrd obtained in step 2, convert it to a XX.trr file and output its first frame as a XX.pdb file. Note that the conversion should only include the protein and nirmatrelvir, excluding water and ions. Modify the filenames referred to by ori_pdb and trr in the contact.py script to obtain the contact map for each mutant.

We are happy to provide assistance if needed. xiayl@ynu.edu.cn.

