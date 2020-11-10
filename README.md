## Create the Flux namespace:
```
$ kubectl create namespace flux
```
## Set the environment variable to the Flux namepace:
```
$ export FLUX_FORWARD_NAMESPACE=flux
```
## Set the GHUSER environment variable to your GitHub or GitLab handle:
```
$ export GHUSER="Your Handle"
```
## Install Flux:
```
$ fluxctl install \
--git-user=${GHUSER} \
--git-email=${GHUSER}@users.noreply.github.com \
--git-url=git@github.com:${GHUSER}/[Your Repo Name] \
--git-path=namespaces,workloads \
--namespace=flux | kubectl apply -f -
```
## Check the rollout status:
```
$ kubectl -n flux rollout status deployment/flux
```
## Obtain the RSA key that was created:
```
$ fluxctl identity --k8s-fwd-ns flux
```
Note: Copy the RSA key and set it up in GitHub as a 'Deploy Key' or in GitLab as an SSH Key. Be sure to grant write access to the key when you add it.
