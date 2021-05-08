# Proyecto-Final-RHP
Repositorio con los archivos necesarios para una implementación completa para la materia de Modelos de Arquitecturas Orientadas a Servicios

# Comandos para ejecutar proyecto:
#Crear maquina virtual:

docker-machine create --driver virtualbox --virtualbox-cpu-count 2 --virtualbox-disk-size 15000 --virtualbox-memory 4096 --virtualbox-boot2docker-url https://releases.rancher.com/os/latest/rancheros.iso ***nombreMaquinaVirtual***

#Cambiar consola de Rancher hacia Ubuntu:

sudo ros console list
sudo ros console switch ubuntu

#Instalar Docker-Compose en Rancher:

sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

#Habilitar la ejecución de GIT en VM:

alias git="docker run -ti --rm -v $(pwd):/git bwits/docker-git-alpine"

#Descargar repositorio de git para logstache:

git clone https://github.com/rodoponce/Proyecto-Final-RHP-.git

#Acomodo de carpetas en maquina virtual:

cd Proyecto-Final-RHP-
sudo mv Dockerfile-logstash ../
sudo mv docker-compose.yml ../
sudo mv README.md ../
sudo mv data/ ../
sudo mv volumes/ ../
cd ..
cd volumes/
sudo mkdir -p volumes/elk-stack/elasticsearch
cd volumes/elk-stack/
sudo chmod 777 elasticsearch/
cd ..
cd ..
sudo rm -rRf Proyecto-Final-RHP-

#Crear Contenedores:

sudo docker-compose up --build -d
