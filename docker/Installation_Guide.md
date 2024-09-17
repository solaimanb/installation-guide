# 🐋 Docker Installation Guide for Kali Linux
![Docker Version](https://img.shields.io/badge/Docker-27.2.1-blue)

This guide provides step-by-step instructions to install Docker on Kali Linux using both the `docker.io` package from the Kali repositories and the `docker-ce` package from the official Docker repository.

## Table of Contents

1. [Installing Docker using docker.io](#installing-docker-using-dockerio)
2. [Installing Docker using docker-ce](#installing-docker-using-docker-ce)
3. [Testing Your Installation](#testing-your-installation)

### Installing Docker using docker.io

1. **Update Package List**:

   ```bash
   sudo apt update
   ```

2. **Install Docker**:

   ```bash
   sudo apt install -y docker.io
   ```

3. **Enable and Start Docker**:

   ```bash
   sudo systemctl enable docker --now
   ```

4. **Add User to Docker Group (Optional)**:

   To use Docker without sudo, add your user to the Docker group:

   ```bash
   sudo usermod -aG docker $USER
   ```

   After running this command, log out and back in for the changes to take effect.

5. **Verify Installation**:

   Check if Docker is installed correctly by running:

   ```bash
   docker --version
   ```

### Installing Docker using docker-ce

`docker-ce` can be installed from the official Docker repository. One important note is that Kali Linux is based on Debian, so we need to use Debian’s current stable version (at the time of writing, this is "bookworm").

1. **Install Required Packages**:

   ```bash
   sudo apt install -y apt-transport-https ca-certificates curl gnupg lsb-release
   ```

2. **Add Docker’s GPG Key**:

   ```bash
   curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
   ```

3. **Add Docker Repository**:

   Replace `bookworm` with your current Debian version codename if necessary.

   ```bash
   echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

4. **Update Package List Again**:

   ```bash
   sudo apt update
   ```

5. **Install Docker CE**:

      ```bash
      sudo apt install -y docker-ce docker-ce-cli containerd.io
      ```

6. **Enable and Start Docker**:

      ```bash
      sudo systemctl enable docker --now
      ```

7. **Add User to Docker Group (Optional)**:

      If you want to run Docker commands without sudo, add your user to the Docker group as mentioned earlier.

8. **Verify Installation**:

      Check if Docker is installed correctly by running:

      ```bash
      docker --version
      ```

   **Testing Your Installation**:

      To confirm that Docker is working properly, run a simple test container:

      ```bash
      sudo docker run hello-world
      ```

This command downloads a test image and runs it in a container, displaying a confirmation message if successful.

By following this guide, you should have a fully functional Docker installation on your Kali Linux system. If you encounter any issues during the installation process, refer to the official [Docker documentation](https://docs.docker.com/get-started) or seek help from the community.
