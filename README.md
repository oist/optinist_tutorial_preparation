# preparation instruction
This repository provides instructions for preparing for the hands-on OptiNiSt tutorial. In the tutorial session, participants will run OptiNiSt using small sample data on their computers. To effectively experience the tutorial, we ask participants to download the Docker all-in-one version. Please follow the instructions (1-6) below and prepare before the tutorial. The Docker image used in this tutorial is relatively large and can be difficult to download where the network is unstable. We strongly recommend downloading the image in a stable network environment.

## preparation
<br>

1. Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/).<br> 
- For Mac users, please note that Docker provides different installers for Intel and Apple silicon cpu.

- Ducumentation for installation of Docker desktop for Windows is [here](https://matsuand.github.io/docs.docker.jp.onthefly/desktop/windows/install/), for Mac is [here](https://matsuand.github.io/docs.docker.jp.onthefly/desktop/mac/install/). Basically just default installation should work. 

<br>

2. Start the Docker Desktop application.<br>
- For M1/2 Mac users, make sure 'Rosetta for x86_64/amd64 emulation on Apple Silicon' is checked in the settings for Docker Desktop. 
<br> 

3. Open a [PowerShell](https://learn.microsoft.com/ja-jp/powershell/scripting/learn/ps101/01-getting-started?view=powershell-7.4) (Windows) or Terminal (Mac/Linux) in your computer and execute the following to fetch the Docker image.

```
docker pull oistncu/optinist-allinone
```
<br>

4. Create and run the container by the following command.
```
docker run -it --shm-size=2G -v YOURSAVINGDIRECTORY:/app/studio_data --env OPTINIST_DIR="/app/studio_data" --name optinist_container -d -p 8000:8000 --restart=unless-stopped oistncu/optinist-allinone:latest poetry run python main.py --host 0.0.0.0 --port 8000
```

- The `-v` option in docker run mounts a path from the host to a path in the container. 
Substitute `YOURSAVINGDIRECTORY` to your own path. 
For example, `C:/tmp`(in Windows) or `/tmp` (in Mac) will assign the temporary directory of the host.
Make sure the folder you assign exists.


- The container automatically starts optinist. When the initialization is finished, they show the logs in the Docker Desktop like this. 
<img src="/Figures/InitializationLog.png" width="80%">

<details>
<summary>How to show logs in Doker Desktop</summary>
To view the log, click on 'optnist_container' in the Containers section.
<img src="/Figures/ShowLog.png" width="80%">
</details>


<br>
5. After you see the logs, open a web browser and go to http://localhost:8000.<br>

<br>

- For the browser, [Google Chrome](https://www.google.com/chrome/) is recommended.
  
<br>

- If you see this, you have successfully launched the application.
<img src="/Figures/FrontPage.png" width="80%">

<br>

- You can stop and restart the optinist container by clicking on the 'Actions' button in Docker Desktop.
<img src="/Figures/StopContainer.png" width="80%">
<br>



<br>
<br>
<br>

6. In addition, please download [sample files](https://drive.google.com/drive/folders/1SUy3GBltprKUOa_KNPqqevGGZURq6oEY?usp=sharing). The files are sample data and workflow.

## trouble shooting
<br>
Issue: The Docker container seems to be working, but http://localhost:8000 does not show the front page of OptiNiSt.<br>
Solution: Try using 127.0.0.1 instead of localhost.<br>
<br>

<details>

## other information 

### OptiNiSt
- [documentation](https://optinist.readthedocs.io/en/latest/ )
- [gitub repository](https://github.com/oist/optinist)

### NWB
- [project](https://www.nwb.org)
- [NWB software](https://nwb-overview.readthedocs.io/en/latest/index.html)
- [HDF view](https://www.hdfgroup.org/downloads/hdfview/)

### cell detection algorithms
&emsp; suite2p &emsp;[website](https://suite2p.readthedocs.io/en/latest/index.html)&emsp;[github repository](https://github.com/MouseLand/suite2p) &emsp; [paper](https://www.biorxiv.org/content/10.1101/061507v2)<br>
&emsp; CaImAn &emsp;[website](https://caiman.readthedocs.io/en/latest/) &emsp;[github repository](https://github.com/flatironinstitute/CaImAn)&emsp;[paper](https://elifesciences.org/articles/38173)<br>
&emsp; lccd &emsp;[gitub repository](https://github.com/magnetizedCell/lccd-python)&emsp; [paper](https://www.sciencedirect.com/science/article/pii/S016801022200075X)<br>
  


