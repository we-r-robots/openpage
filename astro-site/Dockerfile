# ---------- build stage ----------

FROM node:20-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build



# ---------- runtime stage ----------

FROM node:20-alpine

WORKDIR /app

COPY --from=build /app ./

EXPOSE 3000

CMD ["npm","run","preview","--","--host","0.0.0.0","--port","3000"]

