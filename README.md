# library(openxlsx)
library(sparsepca)
library(robCompositions)
library(stats)
x=read.csv("data")
dataclr=cenLR(dataframe,exp(1)) #LCR transformation
write.csv(dataclr$x.clr,"htclrnew.csv")  #save results of LCR transformation

robspca.res=robspca(dataclr$x.clr,k=32,alpha=4e-4,beta=1e-4,gamma=100,verbose=1,max_iter=500,tol=1e-4,center=TRUE,scale=FALSE) # sparse PCA 

print(robspca.res)
write.csv(robspca.res$loadings,"Loadings_clrnew2.csv")
write.csv(robspca.res$scores,"scores_clrnew2.csv")
write.csv(robspca.res$sdev,"Eigenvalues_clrnew2.csv")

